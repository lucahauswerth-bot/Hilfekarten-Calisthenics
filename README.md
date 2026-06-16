[index.html](https://github.com/user-attachments/files/29002067/index.html)
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Analysehilfen – Calisthenics Workout</title>
  <style>
    :root {
      --bg: #080b10;
      --panel: #111821;
      --panel-soft: #17212d;
      --panel-open: #1b2835;
      --text: #f4f8fb;
      --muted: #aab7c4;
      --line: rgba(255, 255, 255, .12);
      --accent: #34e89e;
      --accent-2: #4aa8ff;
      --warning: #ffc857;
      --shadow: 0 22px 60px rgba(0, 0, 0, .34);
      --radius: 8px;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      min-height: 100vh;
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at top left, rgba(52, 232, 158, .18), transparent 30%),
        radial-gradient(circle at bottom right, rgba(74, 168, 255, .16), transparent 32%),
        linear-gradient(135deg, #07090d 0%, #0c1118 45%, #101820 100%);
      line-height: 1.55;
    }

    button,
    input {
      font: inherit;
    }

    button {
      cursor: pointer;
    }

    .page {
      width: min(1120px, calc(100% - 32px));
      margin: 0 auto;
      padding: 42px 0 56px;
    }

    .hero {
      display: grid;
      gap: 14px;
      padding: 26px 0 28px;
      border-bottom: 1px solid var(--line);
    }

    .eyebrow {
      width: fit-content;
      margin: 0;
      padding: 5px 10px;
      border: 1px solid rgba(52, 232, 158, .28);
      border-radius: 999px;
      color: var(--accent);
      background: rgba(52, 232, 158, .08);
      font-size: .82rem;
      font-weight: 800;
      letter-spacing: .04em;
      text-transform: uppercase;
    }

    h1 {
      max-width: 900px;
      margin: 0;
      font-size: clamp(2rem, 6vw, 4.6rem);
      line-height: 1;
      letter-spacing: 0;
    }

    .intro {
      max-width: 780px;
      margin: 0;
      color: var(--muted);
      font-size: clamp(1rem, 2.4vw, 1.18rem);
    }

    .toolbar {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin: 22px 0;
    }

    .progress {
      display: flex;
      align-items: center;
      gap: 10px;
      min-width: min(100%, 340px);
      color: var(--muted);
      font-weight: 700;
    }

    .progress-bar {
      position: relative;
      flex: 1;
      height: 10px;
      overflow: hidden;
      border-radius: 999px;
      background: rgba(255, 255, 255, .1);
    }

    .progress-bar span {
      display: block;
      width: 0%;
      height: 100%;
      border-radius: inherit;
      background: linear-gradient(90deg, var(--accent), var(--accent-2));
      transition: width .3s ease;
    }

    .reset-button {
      min-height: 42px;
      padding: 9px 14px;
      border: 1px solid rgba(255, 255, 255, .18);
      border-radius: var(--radius);
      color: var(--text);
      background: rgba(255, 255, 255, .06);
      transition: transform .18s ease, border-color .18s ease, background .18s ease;
    }

    .reset-button:hover {
      transform: translateY(-1px);
      border-color: rgba(255, 255, 255, .35);
      background: rgba(255, 255, 255, .1);
    }

    .cards {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 18px;
    }

    .help-card {
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: linear-gradient(180deg, rgba(255, 255, 255, .055), rgba(255, 255, 255, .025)), var(--panel);
      box-shadow: var(--shadow);
    }

    .help-card {
      display: grid;
      gap: 16px;
      padding: 20px;
    }

    .card-header {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 16px;
    }

    .card-title {
      margin: 0;
      font-size: 1.2rem;
      line-height: 1.2;
    }

    .card-number {
      display: grid;
      place-items: center;
      flex: 0 0 auto;
      width: 34px;
      height: 34px;
      border-radius: 50%;
      color: #06100c;
      background: var(--accent);
      font-weight: 900;
    }

    .steps {
      display: grid;
      gap: 10px;
    }

    .step {
      border: 1px solid rgba(255, 255, 255, .1);
      border-radius: var(--radius);
      background: var(--panel-soft);
      overflow: hidden;
    }

    .step.is-open {
      border-color: rgba(52, 232, 158, .35);
      background: var(--panel-open);
    }

    .step-button {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      width: 100%;
      min-height: 52px;
      padding: 13px 14px;
      border: 0;
      color: var(--text);
      background: transparent;
      text-align: left;
      font-weight: 850;
    }

    .step-button:hover {
      background: rgba(255, 255, 255, .045);
    }

    .step-button:disabled {
      cursor: not-allowed;
      color: rgba(244, 248, 251, .46);
      background: rgba(0, 0, 0, .12);
    }

    .button-state {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      flex: 0 0 auto;
      width: 28px;
      height: 28px;
      border-radius: 50%;
      color: #071019;
      background: var(--warning);
      font-weight: 950;
    }

    .step.is-open .button-state {
      background: var(--accent);
    }

    .step[hidden] {
      display: none;
    }

    .step-content {
      display: grid;
      grid-template-rows: 0fr;
      border-top: 1px solid transparent;
      transition: grid-template-rows .28s ease, border-color .28s ease;
    }

    .step.is-open .step-content {
      grid-template-rows: 1fr;
      border-color: rgba(255, 255, 255, .1);
    }

    .step-content-inner {
      min-height: 0;
      overflow: hidden;
    }

    .step-text {
      margin: 0;
      padding: 14px;
      color: #dce7ee;
      animation: fadeUp .28s ease both;
      white-space: pre-line;
    }

    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(6px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @media (max-width: 760px) {
      .page {
        width: min(100% - 24px, 1120px);
        padding-top: 24px;
      }

      .cards {
        grid-template-columns: 1fr;
      }

      .hero {
        padding-top: 16px;
      }

      .toolbar {
        align-items: stretch;
      }

      .progress,
      .reset-button {
        width: 100%;
      }
    }

    @media (prefers-reduced-motion: reduce) {
      *,
      *::before,
      *::after {
        scroll-behavior: auto !important;
        transition-duration: .01ms !important;
        animation-duration: .01ms !important;
      }
    }
  </style>
</head>
<body>
  <main class="page">
    <section class="hero" aria-labelledby="page-title">
      <p class="eyebrow">Digitale Hilfekarten</p>
      <h1 id="page-title">Analysehilfen – Calisthenics Workout</h1>
      <p class="intro">Öffnet eine Hilfe nur, wenn ihr bei der Analyse oder Verbesserung eures Workouts nicht weiterkommt.</p>
    </section>

    <section class="toolbar" aria-label="Fortschritt">
      <div class="progress" aria-live="polite">
        <span id="progressText">0 von 12 Hilfen geöffnet</span>
        <div class="progress-bar" aria-hidden="true"><span id="progressBar"></span></div>
      </div>
      <button class="reset-button" type="button" id="resetButton">Fortschritt zurücksetzen</button>
    </section>

    <section class="cards" id="helpCards" aria-label="Hilfebereiche"></section>
  </main>

  <script>
    // Alle Inhalte werden zentral gepflegt, damit Text und Struktur leicht anpassbar bleiben.
    const helpAreas = [
      {
        title: "Muskelgruppencheck",
        steps: [
          {
            label: "Stufe 1: Denkimpuls",
            text: "Überlegt, ob euer Workout den ganzen Körper beansprucht."
          },
          {
            label: "Stufe 2: konkrete Leitfragen",
            text: "Prüft: Sind Push-, Pull-, Legs- und Core-Übungen enthalten?"
          },
          {
            label: "Stufe 3: konkrete Lösungshilfe",
            text: "Wenn eine Kategorie fehlt, ergänzt eine passende Übung:\nPush = Push-up\nPull = Rows / Rudern\nLegs = Squats oder Nordic Hamstring Curl\nCore = Plank oder Sit-up"
          }
        ]
      },
      {
        title: "Belastungscheck",
        steps: [
          {
            label: "Stufe 1: Denkimpuls",
            text: "Überlegt, ob euer Workout eher zu leicht, passend oder zu anstrengend ist."
          },
          {
            label: "Stufe 2: konkrete Leitfragen",
            text: "Prüft: Wie viele Wiederholungen gibt es? Wie lange dauert die Belastung? Gibt es sinnvolle Pausen?"
          },
          {
            label: "Stufe 3: konkrete Lösungshilfe",
            text: "Wenn die Belastung zu hoch ist, reduziert Wiederholungen, verlängert Pausen oder wählt leichtere Varianten. Wenn sie zu niedrig ist, erhöht Wiederholungen, verkürzt Pausen oder wählt schwierigere Varianten."
          }
        ]
      },
      {
        title: "Trainingsmethodencheck",
        steps: [
          {
            label: "Stufe 1: Denkimpuls",
            text: "Überlegt, ob die gewählte Trainingsmethode zum Trainingsziel passt."
          },
          {
            label: "Stufe 2: konkrete Leitfragen",
            text: "Prüft:\nZirkeltraining eignet sich für Ganzkörpertraining.\nIntervalltraining eignet sich für Kraftausdauer.\nAMRAP eignet sich für individuelles Tempo.\nEMOM eignet sich für klare Struktur.\nTabata eignet sich für hohe Intensität in kurzer Zeit."
          },
          {
            label: "Stufe 3: konkrete Lösungshilfe",
            text: "Wenn Methode und Ziel nicht zusammenpassen, ändert entweder die Methode oder passt das Workout so an, dass Ziel und Methode zusammenpassen."
          }
        ]
      },
      {
        title: "Trainingsprinzipiencheck",
        steps: [
          {
            label: "Stufe 1: Denkimpuls",
            text: "Überlegt, ob euer Workout langfristig sinnvoll trainierbar ist."
          },
          {
            label: "Stufe 2: konkrete Leitfragen",
            text: "Prüft:\nIst das Workout individuell anpassbar?\nIst eine Steigerung möglich?\nIst genug Variation vorhanden?\nIst Regeneration berücksichtigt?"
          },
          {
            label: "Stufe 3: konkrete Lösungshilfe",
            text: "Verbessert das Workout, indem ihr leichtere und schwerere Varianten anbietet, Pausen sinnvoll einplant und Möglichkeiten zur Steigerung ergänzt."
          }
        ]
      }
    ];

    const storageKey = "calisthenicsAnalysehilfen.v1";
    const defaultState = {
      openedSteps: {}
    };

    const state = loadState();
    const helpCards = document.querySelector("#helpCards");
    const progressText = document.querySelector("#progressText");
    const progressBar = document.querySelector("#progressBar");
    const resetButton = document.querySelector("#resetButton");

    renderHelpCards();
    updateProgress();

    resetButton.addEventListener("click", () => {
      if (!confirm("Soll der gespeicherte Fortschritt wirklich gelöscht werden?")) return;
      localStorage.removeItem(storageKey);
      window.location.reload();
    });

    function renderHelpCards() {
      helpCards.innerHTML = "";

      helpAreas.forEach((area, areaIndex) => {
        const card = document.createElement("article");
        card.className = "help-card";

        card.innerHTML = `
          <header class="card-header">
            <h2 class="card-title">${area.title}</h2>
            <span class="card-number" aria-hidden="true">${areaIndex + 1}</span>
          </header>
          <div class="steps"></div>
        `;

        const stepsContainer = card.querySelector(".steps");

        area.steps.forEach((step, stepIndex) => {
          const stepId = getStepId(areaIndex, stepIndex);
          const isOpen = Boolean(state.openedSteps[stepId]);
          const isUnlocked = stepIndex === 0 || Boolean(state.openedSteps[getStepId(areaIndex, stepIndex - 1)]);
          const stepElement = document.createElement("section");

          stepElement.className = `step${isOpen ? " is-open" : ""}`;
          stepElement.hidden = !isUnlocked;
          stepElement.innerHTML = `
            <button class="step-button" type="button" ${isOpen ? "aria-expanded=\"true\"" : "aria-expanded=\"false\""}>
              <span>${step.label}</span>
              <span class="button-state" aria-hidden="true">${isOpen ? "✓" : "+"}</span>
            </button>
            <div class="step-content">
              <div class="step-content-inner">
                <p class="step-text">${step.text}</p>
              </div>
            </div>
          `;

          const button = stepElement.querySelector(".step-button");
          button.addEventListener("click", () => openStep(areaIndex, stepIndex));
          stepsContainer.appendChild(stepElement);
        });

        helpCards.appendChild(card);
      });
    }

    function openStep(areaIndex, stepIndex) {
      const stepId = getStepId(areaIndex, stepIndex);
      state.openedSteps[stepId] = true;
      saveState();
      renderHelpCards();
      updateProgress();
    }

    function updateProgress() {
      const totalSteps = helpAreas.length * 3;
      const openedCount = Object.values(state.openedSteps).filter(Boolean).length;
      const percent = Math.round((openedCount / totalSteps) * 100);

      progressText.textContent = `${openedCount} von ${totalSteps} Hilfen geöffnet`;
      progressBar.style.width = `${percent}%`;
    }

    function getStepId(areaIndex, stepIndex) {
      return `area-${areaIndex}-step-${stepIndex}`;
    }

    function loadState() {
      try {
        const savedState = JSON.parse(localStorage.getItem(storageKey));
        return {
          openedSteps: savedState?.openedSteps || {}
        };
      } catch {
        return structuredClone(defaultState);
      }
    }

    function saveState() {
      localStorage.setItem(storageKey, JSON.stringify(state));
    }
  </script>
</body>
</html>
