# 💰 Contexte Métier - Domaine Financier

## Vue d'Ensemble

Ce document fournit le contexte métier nécessaire pour tous les exemples et exercices de la formation QA & IA. Tous les cas d'usage sont basés sur des scénarios réalistes du secteur financier.

---

## 1. Domaines Couverts

### 1.1 Virement Bancaire (SEPA & International)

**Description** : Transfert d'argent d'un compte à un autre, localement ou internationalement.

**Acteurs** :
- Banco source (émetteur)
- Banque destination (récepteur)
- Réseau (SEPA, SWIFT, etc.)

**Données clés** :

| Champ | Format | Exemple | Validation |
|-------|--------|---------|-----------|
| IBAN Source | ISO 13616 | FR14 2004 1010 0505 0001 3M02 606 | Checksum mod 97 |
| IBAN Destination | ISO 13616 | DE89 3704 0044 0532 0130 00 | Checksum mod 97 |
| Montant | Décimal 2 places | 100.50 | >= 0.01, <= 1M |
| Devise | ISO 4217 (3 chars) | EUR, GBP, USD, CHF | Standard ISO |
| BIC (optionnel) | 8-11 chars | SOGEDEFF | Format SWIFT |
| Libellé | Texte | "Paiement facture" | Max 140 chars, ASCII |

**Flux typique** :
```
1. Utilisateur saisit données
2. Validation (IBAN, montant, devise)
3. Vérification solde source
4. Confirmtion 2FA (SMS/Email)
5. Traitement
6. Confirmation bancaire
7. Historique mis à jour
```

**Durée de traitement** :
- SEPA (national) : 1 jour ouvré
- International : 1-5 jours ouvrés selon pays

**Frais** :
- SEPA : généralement gratuit
- International : 5-50€ (dépend banque)

---

### 1.2 Authentification Multi-Facteurs (2FA/MFA)

**Description** : Sécuriser l'accès en demandant 2 preuves d'identité.

**Méthodes disponibles** :

#### SMS OTP (One-Time Password)
- Code 6-8 chiffres
- Valide 5-15 minutes
- Utilisateur reçoit via SMS
- Approche : Time-based (TOTP) ou Counter-based (HOTP)

#### Email OTP
- Lien cliquable ou code numérique
- Valide 15-30 minutes
- Plus sécurisé que SMS (pas de SIM swap)

#### Biométrie
- Empreinte digitale
- Reconnaissance faciale
- Iris
- Pas d'expiration

#### Questions de Sécurité
- Réponses pré-enregistrées
- Cas limites : changement d'adresse
- Moins sûr, legacy

**Cas d'usage** :
- Authentification première connexion
- Connexion depuis appareil nouveau
- Transaction importante (paiement > 1000€)
- Changement mot de passe

**Taux de succès réaliste** :
- Premier essai : 95%
- Avec retry : 98%
- Abandon sans complétion : 2%

---

### 1.3 Calcul d'Intérêts

**Description** : Calcul du rendement sur une épargne ou un crédit.

**Formules** :

#### Intérêt Simple
```
I = Principal × Taux × Temps
```

#### Intérêt Composé
```
A = P(1 + r/n)^(nt)
```

**Paramètres** :
- Principal : montant initial
- Taux annuel : % par an
- Période : mensuelle, trimestrielle, annuelle
- Durée : jours, mois, années

**Exemples** :
```
- 1000€ à 2% par an → 20€/an
- 10000€ à 3% trimestriel → ~300€/trimestre
- Livret épargne: 3-4.5% annuel
- Crédit personnel: 5-15% annuel
```

**Méthodes de calcul** :
- ACT/ACT : Jours réels / 365 ou 366
- 30/360 : Mois standardisés à 30 j, ans à 360 j
- Exact/360 : Jours exacts / 360

**Cas de test** :
- Calcul pour 1 jour
- Calcul pour année bissextile (366 j)
- Changement de taux (hypothèque variable)
- Arrondis (2-3 décimales)

---

### 1.4 Conformité & Régulations

#### PCI DSS (Payment Card Industry Data Security Standard)

**Objectif** : Protéger les données de carte bancaire.

**Principes clés** :
- Jamais stocker le PAN (Primary Account Number) en clair
- Tokenization requise
- Chiffrement en transit (TLS 1.2+)
- Chiffrement au repos
- Audit logs obligatoires

**Pour nos tests** :
- Utiliser données fictives
- Jamais des cartes réelles
- Tester rejet des PANs partiels
- Vérifier que la 2FA est active

#### AML (Anti-Money Laundering)

**Objectif** : Détecter et prévenir les activités illégales.

**Seuils typiques** :
- Alerte si transaction > 50 000€
- Alerte si 10 transactions de 10k€ en 24h
- Validation KYC (Know Your Customer)

**Cas de test** :
- Transaction de montant élevé → nécessite vérification
- Patterns suspects (structuring) → blocage
- Données KYC incomplètes → rejet

#### GDPR (Règlement Général sur la Protection des Données)

**Droits** :
- Droit d'accès aux données
- Droit à l'oubli (suppression)
- Portabilité des données
- Rectification

**Pour nos tests** :
- Données personnelles anonymisées
- Consentement explicite simulé
- Right to delete implementé
- Audit trails conservés

---

### 1.5 Gestion de Portefeuille (Optionnel)

**Description** : Gestion d'actifs financiers (actions, obligations, crypto).

**Éléments** :
- Valorisation en temps réel
- Rendements (dividendes, intérêts)
- Allocation d'actifs
- Rebalancement

**Cas de test** :
- Prix change en temps réel
- Détection de volatilité
- Ordre d'achat/vente
- Frais appliqués

---

## 2. Normes & Standards

### IBAN (International Bank Account Number) - ISO 13616

**Structure** :
```
[CC][2-digit checksum][Country-specific details]
```

**Longueurs par pays** :
- France : 27 caractères
- Allemagne : 22 caractères
- Espagne : 24 caractères
- Italie : 27 caractères

**Checksum validation** (Luhn) :
```
1. Déplacer les 4 premiers chars à la fin
2. Remplacer lettres par chiffres (A=10, B=11, etc.)
3. Calculer mod 97
4. Résultat doit être 1
```

**Exemples valides** :
```
FR14 2004 1010 0505 0001 3M02 606
DE89 3704 0044 0532 0130 00
IT60 X054 2811 1010 0000 0123 456
ES91 2100 0418 4502 0005 1332
```

---

### BIC (Business Identifier Code) - ISO 9362

**Format** : `[4 Bank Code][2 Country][2 Location][3 Branch-optional]`

**Exemples** :
```
SOGEDEFF    → Société Générale, France, Défense (HQ)
BNPADEFF    → BNP Paribas, France, Défense
DEUTDEFF    → Deutsche Bank, Allemagne, Francfort
CHVBCHZH    → UBS, Switzerland, Zurich
```

---

### Devise - ISO 4217

**Codes 3 caractères** :
- EUR : Euro
- GBP : Livre Sterling
- USD : Dollar américain
- CHF : Franc suisse
- JPY : Yen japonais

---

## 3. Données de Test Réalistes

### IBANs de Test (SEPA)

```
Pays        IBAN                                    Checksum Valide
France      FR14 2004 1010 0505 0001 3M02 606      ✓ Valide
Allemagne   DE89 3704 0044 0532 0130 00            ✓ Valide
Italie      IT60 X054 2811 1010 0000 0123 456      ✓ Valide
Espagne     ES91 2100 0418 4502 0005 1332          ✓ Valide
Belgique    BE68 5390 0754 7034                    ✓ Valide
Pays-Bas    NL91 ABNA 0417 1643 00                 ✓ Valide
```

### Montants de Test

```json
{
  "valides": {
    "minimum": 0.01,
    "courant": [10.50, 50.00, 100.00, 500.00],
    "important": [5000.00, 50000.00],
    "maximum": 999999.99
  },
  "invalides": {
    "negatif": -50.00,
    "zero": 0.00,
    "depassement": 1000000.01,
    "precision": 10.555
  },
  "limites": {
    "min_valide": 0.01,
    "max_valide": 999999.99,
    "seuil_alerte_aml": 50000.00
  }
}
```

### BICs de Test

```
SOGEDEFF    → Société Générale (valide)
BNPADEFF    → BNP Paribas (valide)
CBKOFR76    → Crédit du Nord (valide)
PCHQFR2S    → Banque Pchq (valide)
INVALIDXX   → BIC invalide (format correct, banque fictive)
```

---

## 4. Scénarios de Test Métier

### Scénario 1 : Virement Simple (Positif)

```
Préconditions :
- Utilisateur connecté
- Compte source: 5000€
- Compte destination: vide
- Pas de limite quotidienne

Actions :
1. Nouvesu virement
2. Destinataire: "John Doe"
3. IBAN: FR1420041010050500013M02606
4. Montant: 100€
5. Devise: EUR
6. Confirmer
7. Entrer code 2FA

Résultat attendu :
- Message succès
- Compte source: 4900€
- Compte destination: +100€
- Historique mis à jour
```

---

### Scénario 2 : IBAN Invalide (Négatif)

```
Préconditions :
- Formulaire ouvert

Actions :
1. Saisir IBAN: "XX99INVALID00000000"
2. Cliquer continuer

Résultat attendu :
- Erreur: "IBAN invalide"
- Checksum non valide
- Champ highlight en rouge
```

---

### Scénario 3 : Montant Dépassant Limite (Négatif)

```
Préconditions :
- Limite quotidienne: 100k€
- Solde: 500k€

Actions :
1. Saisir montant: 150k€
2. Confirmer

Résultat attendu :
- Erreur: "Montant > limite quotidienne (100k€)"
- Suggestion: "Fractionner en 2 virements"
```

---

### Scénario 4 : 2FA Expiré (Négatif)

```
Préconditions :
- Virement en attente de confirmation
- Code OTP expié (> 15 min)

Actions :
1. Saisir ancien code

Résultat attendu :
- Erreur: "Code expiré, demander un nouveau"
- Bouton "Renvoyer code"
```

---

### Scénario 5 : Transaction Suspecte (AML) (Négatif)

```
Préconditions :
- Seuil AML: 50k€
- Aucune transaction récente
- Transactions jour < 50k€

Actions :
1. Créer virement de 60k€

Résultat attendu :
- Transaction acceptée
- Vérification supplémentaire KYC demandée
- Attente modération: 24-48h
```

---

## 5. Calculs Exemples

### Calcul d'Intérêt Simple

```
Principal: 1000€
Taux annuel: 2%
Durée: 1 an

Intérêt = 1000 × 0.02 × 1 = 20€
Montant final = 1020€
```

### Calcul d'Intérêt Composé (Trimestriel)

```
Principal: 10000€
Taux annuel: 3%
Périodes par an: 4 (trimestriel)
Durée: 1 an

A = 10000 × (1 + 0.03/4)^(4×1)
A = 10000 × (1.0075)^4
A ≈ 10303.66€
```

---

## 6. Termes Métier Clés

| Terme | Définition | Exemple |
|-------|-----------|---------|
| **SEPA** | Single Euro Payments Area | Virements EUR zone Euro |
| **SWIFT** | Société pour télécommunications financières | Virements internationaux |
| **PAN** | Primary Account Number | Numéro carte (16 digits) |
| **Tokenization** | Remplacer données sensibles par token | 4532... → TOKEN_12345 |
| **KYC** | Know Your Customer | Vérification identité client |
| **AML** | Anti-Money Laundering | Détection activités suspectes |
| **OTP** | One-Time Password | Code temporaire 2FA |
| **TOTP** | Time-based OTP | OTP basé sur l'heure |
| **Escrow** | Compte tiers | Fond en attente libération |
| **Arbitrage** | Exploiter écarts prix | Acheter EUR/USD, vendre USD/EUR |

---

## 7. Ressources de Référence

### Standards Officiels
- [ISO 13616 - IBAN](https://www.iso.org/standard/81090.html)
- [ISO 9362 - BIC](https://www.iso.org/standard/36510.html)
- [ISO 4217 - Devises](https://www.iso.org/iso-4217-currency-codes.html)

### Réglementations
- [PCI DSS v3.2.1](https://www.pcisecuritystandards.org/)
- [GDPR](https://gdpr-info.eu/)
- [AML/CFT Directives](https://ec.europa.eu/info/business-economy-euro/banking-and-finance/financial-supervision-and-risk-management/anti-money-laundering-and-counter-terrorist-financing_en)

### Outils de Validation
- [IBAN Validator](https://www.iban.com/iban-checker) - Vérifier IBAN en ligne
- [BIC Finder](https://www.bic-code.com/) - Trouver BIC par banque

---

**Version** : 1.0 | **Date** : 16 Nov 2025 | **Maintenance** : À jour
