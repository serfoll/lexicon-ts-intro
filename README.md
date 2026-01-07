# Uppgift: Kom igång med TypeScript

**Mål:** I den här uppgiften ska du installera nödvändiga verktyg, sätta upp ett nytt projekt från grunden och se till att din TypeScript-kod kan köras i webbläsaren.

---

## Steg 1: Kontrollera Node.js och npm

Först måste vi se till att du har Node.js installerat på din dator.

1. [x] Öppna din terminal (Mac) eller PowerShell/Command Prompt (Windows).
2. [x] Skriv följande kommando och tryck Enter:
   ```bash
   node -v
   npm -v
   ```

Resultat: Om du får tillbaka versionsnummer (t.ex. v20.x.x) är du redo för nästa steg.

Om du får felmeddelande: Gå till nodejs.org och ladda ner "LTS"-versionen. (Rekommenderar v22.x.x).

## Steg 2: Skapa projektmapp och initiera npm

Nu ska vi skapa mappen där din kod ska bo.

1. [x] Skapa en ny mapp på datorn som heter `ts-intro` (eller valfritt namn).
2. [x] Öppna denna mapp i **VS Code**.
3. [x] Öppna terminalen inuti VS Code (`Terminal` -> `New Terminal`).
4. [x] Initiera ett nytt projekt genom att skriva:

   ```bash
   npm init -y
   ```

   Detta skapar en fil som heter package.json

## Steg 3: Installera TypeScript

Nu ska vi hämta TypeScript-verktygen till just det här projektet.

1. [x] I terminalen, skriv:
   ```bash
   npm install typescript --save-dev
   ```
   Du ser nu att en mapp som heter node_modules har dykt upp. Det är där verktygen ligger.

## Steg 4: Initiera TypeScript-konfigurationen

Vi behöver en `tsconfig.json` som berättar för datorn hur den ska översätta vår kod.

1. [x] I terminalen, skriv:
   ```bash
   npx tsc --init
   ```

## Steg 5: Konfigurera tsconfig.json

Nu ska vi ställa in så att TypeScript beter sig modernt och strikt.

1. [x] Öppna filen `tsconfig.json` som skapades.
2. [x] Ta bort allt innehåll i filen och klistra in nedanstående kod istället:

```json
{
  "compilerOptions": {
    "rootDir": "./src",
    "outDir": "./dist",
    "module": "es2022",
    "target": "es2022",
    "strict": true,
    "esModuleInterop": true
  }
}
```

## Steg 6: Skapa filstruktur och kod

Nu ska vi skapa själva koden.

1. [x] Skapa en ny mapp i ditt projekt som heter `src`.
2. [x] Inuti `src`, skapa en fil som heter `index.ts`.
3. [x] I roten av projektet (utanför src), skapa en fil som heter `index.html`.

**Klistra in detta i `src/index.ts`:**

```typescript
let courseName: string = 'Frontendutveckling'
let studentsEnrolled: number = 25
let isTypeScriptFun: boolean = true

console.log(`Kurs: ${courseName}`)
console.log(`Antal studenter: ${studentsEnrolled}`)

function greetStudent(name: string): string {
  return `Välkommen, ${name}!`
}

console.log(greetStudent('Alice'))
```

## Steg 7: Kompilera och Kör

Nu är sanningens ögonblick.

1. [x] Vi måste översätta TS till JS. Skriv i terminalen:
   ```bash
   npx tsc
   ```

**Klistra in detta i `index.html`:**

```html
<!DOCTYPE html>
<html lang="sv">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>TypeScript Intro</title>
    <script type="module" src="./dist/index.js" defer></script>
  </head>
  <body>
    <h1>Öppna med live server för att se resultatet!</h1>
    <p>Högerklicka > Inspektera > Console</p>
  </body>
</html>
```

## Steg 8: Testa Breakpoints (Felsökning)

Nu ska vi testa att pausa koden medan den körs för att se vad som händer "under huven".

1. [x] Stanna kvar i webbläsarens utvecklarverktyg (F12) och klicka på fliken som heter **Sources**.
2. [x] I menyn till vänster, leta upp mappen `dist` och klicka på `index.js`.
       _(Tips: Du kan också trycka `Ctrl + P` (PC) eller `Cmd + P` (Mac) och skriva "index" för att söka fram filen direkt)._
3. [x] Klicka på **radnumret** bredvid raden där det står `return ...`. En färgad markering tänds. Du har nu satt en **Breakpoint**.
4. [x] Ladda om sidan (tryck `F5` eller `Cmd + R`).
5. [x] Sidan kommer sluta ladda och koden "fryser" vid din markering.
6. [x] Håll muspekaren över variabeln `name` i koden. Ser du att det står "Alice"?
7. [x] Tryck på **Play-knappen** (▶️) ute till höger i panelen för att låta koden köra klart.
