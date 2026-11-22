# KNML — Król Ławki

> Projekt gry 2D tworzony w ramach koła naukowego z wykorzystaniem **Godot Engine 4.7.2 .NET** oraz biblioteki **Godot RL Agents**.

---

## 1. Wymagania wstępne

* **Godot Engine 4.7.2 .NET** (wersja z obsługą C# / Mono — konieczna do budowania projektu i uruchamiania modeli `.onnx`).
* **Python 3.10** (zalecana wersja dla pełnej kompatybilności z `godot-rl`, `stable-baselines3` i `torch`).
* **.NET SDK** oraz **Git**.

---

## 2. Uruchomienie projektu po sklonowaniu

Repozytorium zawiera już skonfigurowaną wtyczkę `addons/godot_rl_agents` oraz zależność `Microsoft.ML.OnnxRuntime` w pliku projektu `.csproj`.

### Krok 1: Konfiguracja środowiska Python (`venv`)

W głównym katalogu repozytorium utwórz i aktywuj środowisko wirtualne, a następnie zainstaluj wymagane biblioteki:

**Windows (`cmd`):**
```bat
py -3.10 -m venv venv
venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```

**Linux (`bash`/`zsh`):**
```bash
python3.10 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

### Krok 2: Otwarcie i budowanie projektu w Godocie

1. Uruchom **Godot Engine 4.7.2 .NET**, kliknij **Importuj** i wskaż plik `project.godot` z głównego folderu repozytorium.
2. W górnym menu sprawdź **Projekt -> Ustawienia projektu... -> Wtyczki** — upewnij się, że wtyczka **GodotRLAgents** jest zaznaczona jako **Włączona**.
3. Kliknij ikonę **młotka** (*Buduj* / *Build*) w prawym górnym rogu edytora, aby skompilować solucję C# (panel **MSBuild** powinien zakończyć budowanie bez błędów).

### Krok 3: Uruchomienie treningu RL (opcjonalnie)

1. W terminalu z aktywnym `(venv)` uruchom serwer treningowy:
   ```bash
   gdrl --viz
   ```
2. W edytorze Godot uruchom projekt klawiszem **F5** (przycisk *Play*).

---

## 3. Zasady pracy z branchami (Git Workflow)

* **Gałąź `main`** przechowuje wyłącznie stabilną, przetestowaną i budującą się wersję projektu — **nie pushujemy zmian bezpośrednio na `main`**.
* **Nowe zadania i poprawki** realizujemy na osobnych branchach tworzonych zawsze z aktualnego `main`:
  * `feat/krotki-opis` — nowa funkcjonalność (np. `feat/ruch-gracza`, `feat/srodowisko-rl`)
  * `fix/krotki-opis` — poprawka błędu (np. `fix/kolizje-areny`)
  * `docs/krotki-opis` — zmiany w dokumentacji
* **Łączenie zmian (Pull Request):**
  1. Wypchnij swój branch na GitHuba (`git push -u origin nazwa-brancha`).
  2. Otwórz **Pull Request** do gałęzi `main`.
  3. Poproś inną osobę z zespołu o krótkie **code review** i sprawdzenie, czy projekt po zmianach poprawnie się buduje przed wykonaniem merge'a.