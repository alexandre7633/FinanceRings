# FinanceRings// ======================================================
// Finance Rings
// Version : 0.1
// Auteur : Alexandre + ChatGPT
// ======================================================

// -----------------------------------------------------------------------------
// Données (elles seront déplacées dans data.json à partir de la v0.2)
// -----------------------------------------------------------------------------

const objectifs = [
  {
    nom: "Sécurité",
    actuel: 14500,
    objectif: 20000,
    couleur: "#34C759"
  },
  {
    nom: "Enfants",
    actuel: 16200,
    objectif: 30000,
    couleur: "#0A84FF"
  },
  {
    nom: "Projet",
    actuel: 20500,
    objectif: 50000,
    couleur: "#FF9F0A"
  },
  {
    nom: "Retraite",
    actuel: 28000,
    objectif: 100000,
    couleur: "#BF5AF2"
  },
  {
    nom: "Liberté",
    actuel: 31500,
    objectif: 50000,
    couleur: "#FFD60A"
  }
]

// -----------------------------------------------------------------------------
// Calcul du patrimoine
// -----------------------------------------------------------------------------

const patrimoine = objectifs.reduce(
  (total, objectif) => total + objectif.actuel,
  0
)

// -----------------------------------------------------------------------------
// Widget
// -----------------------------------------------------------------------------

const widget = new ListWidget()

widget.backgroundColor = new Color("#111111")
widget.setPadding(16, 16, 16, 16)

// -----------------------------------------------------------------------------
// Titre
// -----------------------------------------------------------------------------

const titre = widget.addText("💰 Finance Rings")

titre.font = Font.boldSystemFont(20)
titre.textColor = Color.white()

widget.addSpacer(12)

// -----------------------------------------------------------------------------
// Liste provisoire des objectifs
// -----------------------------------------------------------------------------

for (const objectif of objectifs) {

  const progression = Math.round(
    (objectif.actuel / objectif.objectif) * 100
  )

  const ligne = widget.addStack()

  const point = ligne.addText("● ")
  point.textColor = new Color(objectif.couleur)

  const texte = ligne.addText(
    `${objectif.nom}  ${progression}%`
  )

  texte.textColor = Color.white()
  texte.font = Font.systemFont(13)

  widget.addSpacer(4)
}

widget.addSpacer()

// -----------------------------------------------------------------------------
// Patrimoine
// -----------------------------------------------------------------------------

const patrimoineTexte = widget.addText(
  `Patrimoine : ${patrimoine.toLocaleString("fr-FR")} €`
)

patrimoineTexte.font = Font.boldSystemFont(13)
patrimoineTexte.textColor = Color.white()

// -----------------------------------------------------------------------------
// Affichage
// -----------------------------------------------------------------------------

Script.setWidget(widget)
widget.presentMedium()
Script.complete()
