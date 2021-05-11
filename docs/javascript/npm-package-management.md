---
title: Zarządzanie pakietami npm
description: Visual Studio ułatwia zarządzanie pakietami przy użyciu menedżera pakietów Node.js (npm)
ms.custom: seodec18
ms.date: 02/23/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2fcf1bd9e9ef5c3ff0663cf12684e6e638d1e5e4
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729289"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Zarządzanie pakietami npm w programie Visual Studio

Program npm umożliwia instalowanie pakietów i zarządzanie nimi do użycia w Node.js aplikacji. Visual Studio ułatwia interakcję z programem npm i wydawanie poleceń npm za pośrednictwem interfejsu użytkownika lub bezpośrednio. Jeśli nie masz informacji o programie npm i chcesz dowiedzieć się więcej, przejdź do [dokumentacji programu npm.](https://docs.npmjs.com/)

Visual Studio z programem npm różni się w zależności od typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otwieranie folderu (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> Program npm oczekuje *node_modules* i *package.jsw katalogu* głównym projektu. Jeśli struktura folderów aplikacji jest inna, należy zmodyfikować strukturę folderów, jeśli chcesz zarządzać pakietami npm przy użyciu Visual Studio.

## <a name="nodejs-projects"></a>Node.js projektów

W Node.js projektach można wykonywać następujące zadania:
* [Instalowanie pakietów z Eksplorator rozwiązań](#npmInstallWindow)
* [Zarządzanie zainstalowanymi pakietami z Eksplorator rozwiązań](#solutionExplorer)
* [Użyj polecenia `.npm` w oknie Node.js interakcyjnego](#interactive)

Te funkcje współpracują ze sobą i synchronizują się z systemem projektu i *package.jsw pliku* w projekcie.

### <a name="prerequisites"></a>Wymagania wstępne

Aby dodać **obsługęNode.js** npm do projektu, musisz zainstalować Node.js dewelopera i środowisko uruchomieniowe programu . Aby uzyskać szczegółowe instrukcje, [zobacz Tworzenie Node.js projektu](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> W przypadku Node.js projektów użyj szablonu rozwiązania Z istniejącego kodu **Node.js** lub typu projektu Otwórz [folder (Node.js),](../javascript/develop-javascript-code-without-solutions-projects.md) aby włączyć w projekcie program npm.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Instalowanie pakietów z Eksplorator rozwiązań (Node.js)

W Node.js projektów najprostszym sposobem instalowania pakietów npm jest zainstalowanie go w oknie instalacji pakietu npm. Aby uzyskać dostęp do tego okna, kliknij prawym przyciskiem myszy **węzeł npm** w projekcie i wybierz polecenie **Zainstaluj nowe pakiety npm.**

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Instalowanie nowego pakietu npm z eksploratora rozwiązań" border="true":::

W tym oknie możesz wyszukać pakiet, określić opcje i zainstalować pakiet.

![Zrzut ekranu przedstawiający okno dialogowe Instalowanie nowych pakietów npm. Zostanie wybrany pakiet azure 2.2.1-preview, a zostaną wyświetlone szczegóły i opcje dla tego pakietu.](../javascript/media/search-package.png)

* **Typ zależności —** wybierz pakiet **Standardowy,** **Deweloper** i **Opcjonalny.** Standardowa określa, że pakiet jest zależnością środowiska uruchomieniowego, podczas gdy Development określa, że pakiet jest wymagany tylko podczas opracowywania.
* **Dodaj do package.js—** zalecane. Ta konfigurowalna opcja jest przestarzała.
* **Wybrana wersja** — wybierz wersję pakietu, który chcesz zainstalować.
* **Inne argumenty npm** — określ inne standardowe argumenty npm. Na przykład możesz wprowadzić wartość wersji, taką jak , aby zainstalować określoną wersję, która `@~0.8` nie jest dostępna na liście wersji.

Postęp instalacji można zobaczyć w danych wyjściowych  **npm** w oknie Dane wyjściowe (aby otworzyć okno, wybierz pozycję **Wyświetl** dane wyjściowe lub  >   naciśnij **klawisze Ctrl**  +  **Alt**  +  **O**). Może to potrwać jakiś czas.

![Dane wyjściowe npm](../javascript/media/npm-output.png)

> [!TIP]
> Pakiety o zakresie można wyszukiwać, dołączając zapytanie wyszukiwania do zakresu, który Cię interesuje, na przykład wpisz , aby wyszukać pliki definicji języka TypeScript dla `@types/mocha` makiety. Ponadto podczas instalowania definicji typów dla języka TypeScript można określić wersję języka TypeScript, która ma być wersją określania wartości docelowej, dodając `@ts2.6` ją w polu argumentu npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Zarządzanie zainstalowanymi pakietami w Eksplorator rozwiązań (Node.js)

Pakiety npm są wyświetlane w Eksplorator rozwiązań. Wpisy w **węźle npm** naśladują zależności w *package.jspliku.*

![Zrzut ekranu przedstawiający węzeł npm w Eksplorator rozwiązań ze stanem instalacji pakietów npm.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stan pakietu

* ![Zainstalowany pakiet](../javascript/media/installed-npm.png) — Zainstalowane i wymienione w package.jsna
* ![Pakiet dodatkowy — ](../javascript/media/extraneous-npm.png) zainstalowany, ale nie wymieniony jawnie w package.jsna
* ![Brak pakietu](../javascript/media/missing-npm.png) - Nie zainstalowano, ale na liście package.jsna

::: moniker range=">=vs-2019"
Kliknij prawym przyciskiem myszy **węzeł npm,** aby podjąć jedną z następujących czynności:

* **Instalowanie nowych pakietów npm** Otwiera interfejs użytkownika w celu zainstalowania nowych pakietów.
* **Instalowanie pakietów npm** Uruchamia polecenie npm install, aby zainstalować wszystkie pakiety wymienione wpackage.js *na .* (Uruchamia `npm install` . )
* **Aktualizowanie pakietów npm** Aktualizuje pakiety do najnowszych wersji zgodnie z zakresem semantyki wersji (SemVer) określonym w *package.jsna .* (Uruchamia `npm update --save` .). Zakresy SemVer są zwykle określane przy użyciu wartości "~" lub "^". Aby uzyskać więcej informacji, [package.jskonfiguracji](../javascript/configure-packages-with-package-json.md).

Kliknij prawym przyciskiem myszy węzeł pakietu, aby podjąć jedną z następujących czynności:

* **Instalowanie pakietów npm** Uruchamia polecenie npm install, aby zainstalować wersję pakietu wymienioną w *package.jsna .* (Uruchamia `npm install` . )
* **Aktualizowanie pakietów npm** Aktualizuje pakiet do najnowszej wersji zgodnie z zakresem SemVer określonym wpackage.js *na .* (Uruchom `npm update --save` ). Zakresy SemVer są zwykle określane przy użyciu wartości "~" lub "^".
* **Odinstalowywanie pakietów npm** Odinstalowuje pakiet i usuwa go zpackage.js *na* (uruchamia `npm uninstall --save` . )
::: moniker-end
::: moniker range="vs-2017"
Kliknij prawym przyciskiem myszy węzeł pakietu lub **węzeł npm,** aby podjąć jedną z następujących czynności:
* **Zainstaluj brakujące pakiety** wymienione wpackage.js *na stronie*
* **Aktualizowanie pakietów npm** do najnowszej wersji
* **Odinstalowywanie pakietu** i usuwanie z *package.jsna*
::: moniker-end

>[!NOTE]
> Aby uzyskać pomoc w rozwiązywaniu problemów z pakietami npm, zobacz [Rozwiązywanie problemów](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Użyj polecenia .npm w Node.js oknie interaktywnym (Node.js)

Możesz również użyć polecenia `.npm` w oknie Node.js interakcyjnego, aby wykonać polecenia npm. Aby otworzyć okno, kliknij prawym przyciskiem myszy projekt w programie Eksplorator rozwiązań wybierz polecenie **Otwórz** Node.js okno interaktywne (lub naciśnij **klawisze Ctrl**  +  **K,** **N**).

W oknie można użyć poleceń, takich jak następujące, aby zainstalować pakiet:

`.npm install azure@4.2.3`

 > [!Tip]
 > Domyślnie program npm będzie wykonywany w katalogu macierzystym projektu. Jeśli masz wiele projektów w rozwiązaniu, określ nazwę lub ścieżkę projektu w nawiasach kwadratowych.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Jeśli projekt nie zawiera pliku package.js, użyj funkcji , aby utworzyć nową package.js`.npm init -y` pliku z wpisami domyślnymi.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core

W przypadku projektów takich ASP.NET Core można zintegrować obsługę npm w projekcie i zainstalować pakiety za pomocą programu npm.
* [Dodawanie obsługi npm do projektu](#npmAdd)
* [Instalowanie pakietów przy użyciu package.jsna](#npmInstallPackage)

>[!NOTE]
> W ASP.NET Core można również użyć [](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) Menedżera bibliotek lub yarn zamiast menedżera npm, aby zainstalować pliki JavaScript i CSS po stronie klienta.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> Dodawanie obsługi npm do projektu (ASP.NET Core)

Jeśli projekt nie zawiera jeszcze pliku *package.js,* możesz dodać go, aby włączyć obsługę npm, dodającpackage.js *pliku* do projektu.

1. Jeśli nie masz zainstalowanych Node.js, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js, ](https://nodejs.org/en/download/) aby uzyskać najlepszą zgodność z zewnętrznymi platformami i bibliotekami.

   Npm wymaga Node.js.

1. Aby dodać *package.jspliku,* kliknij prawym przyciskiem myszy projekt w programie Eksplorator rozwiązań wybierz polecenie Dodaj nowy element  >   (lub naciśnij **klawisze Ctrl**  +  **SHIFT**  +  **A**). Wybierz plik **konfiguracji npm,** użyj nazwy domyślnej, a następnie kliknij przycisk **Dodaj**.

   ![Dodawanie package.jsdo projektu](../javascript/media/npm-add-package-json.png)

   Jeśli nie widzisz pliku konfiguracji npm na liście, Node.js nie są zainstalowane. Możesz użyć tej Instalator programu Visual Studio, aby dodać **Node.js tworzenia** aplikacji. Następnie powtórz poprzedni krok.

1. Uwzględnij co najmniej jeden pakiet npm w sekcji lubpackage.js`dependencies` `devDependencies` w *programie*. Na przykład do pliku można dodać następujące elementy:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Podczas zapisywania pliku program Visual Studio pakiet w **węźle Zależności/npm** w Eksplorator rozwiązań. Jeśli węzeł nie jest wyświetlony, kliknij prawym przyciskiem myszy pozycjępackage.js **i** wybierz **polecenie Przywróć pakiety.**

>[!NOTE]
> W niektórych scenariuszach Eksplorator rozwiązań może nie pokazywać poprawnego stanu zainstalowanych pakietów npm. Aby uzyskać więcej informacji, zobacz temat [Rozwiązywanie problemów](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalowanie pakietów przy użyciu package.jsna (ASP.NET Core)

W przypadku projektów z dołączonym programem npm można skonfigurować pakiety npm przy użyciu programu `package.json` . Kliknij prawym przyciskiem myszy węzeł npm w Eksplorator rozwiązań i wybierz polecenie **Otwórz package.jsna stronie**.

![Zrzut ekranu przedstawiający Eksplorator rozwiązań z wybranym węzłem npm. Zostanie otwarte menu kontekstowe dostępne po kliknięciu prawym przyciskiem myszy, a package.jspozycję Otwórz.](../javascript/media/npm-add-package.png)

Funkcja IntelliSense *package.jsna* ułatwia wybranie określonej wersji pakietu npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Wybieranie wersji pakietu npm" border="true":::

Podczas zapisywania pliku program Visual Studio pakiet w **węźle Zależności/npm** w Eksplorator rozwiązań. Jeśli węzeł nie jest wyświetlony, kliknij prawym przyciskiem myszy pozycję **package.jsi** wybierz **polecenie Przywróć pakiety.**

Instalacja pakietu może potrwać kilka minut. Sprawdź postęp instalacji pakietu, przełączając się na dane **wyjściowe npm** w **oknie Dane** wyjściowe.

![Dane wyjściowe npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Rozwiązywanie problemów z pakietami npm

* Npm wymaga Node.js jeśli nie masz zainstalowanego programu Node.js, zalecamy zainstalowanie wersji LTS z witryny internetowej [ programuNode.js](https://nodejs.org/en/download/) w celu zapewnienia najlepszej zgodności z zewnętrznymi platformami i bibliotekami.

* W Node.js projektach musisz mieć **zainstalowaneNode.js tworzenia** aplikacji na potrzeby obsługi npm.

* W niektórych scenariuszach Eksplorator rozwiązań może nie pokazywać poprawnego stanu zainstalowanych pakietów npm z powodu znanego problemu opisanego [tutaj.](https://github.com/aspnet/Tooling/issues/479) Na przykład pakiet może być wyświetlany jako nieinstalowany podczas instalacji. W większości przypadków można zaktualizować Eksplorator rozwiązań, usuwającpackage.jsna *stronie*, ponownie uruchamiając program  Visual Studio i ponownie dodającpackage.jsdo pliku zgodnie z opisem we wcześniejszej część tego artykułu. Podczas instalowania pakietów można też sprawdzić stan instalacji za pomocą okna dane wyjściowe npm.

* W niektórych ASP.NET scenariuszach podstawowych węzeł npm w Eksplorator rozwiązań może nie być widoczny po skompilowaniu projektu. Aby węzeł był ponownie widoczny, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Unload Project (Zwolnij projekt).** Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Załaduj ponownie projekt**.

* Jeśli podczas kompilowania aplikacji lub transkompilowania kodu TypeScript występują błędy, sprawdź, czy niezgodność pakietu npm jest potencjalnym źródłem błędów. Aby ułatwić identyfikację błędów, sprawdź okno npm Output (Dane wyjściowe npm) podczas instalowania pakietów, zgodnie z wcześniejszym opisem w tym artykule. Jeśli na przykład co najmniej jedna wersja pakietu npm jest przestarzała i powoduje błąd, może być konieczne zainstalowanie najnowszej wersji w celu naprawienia błędów. Aby uzyskać informacje na temat *używaniapackage.jsna do* kontrolowania wersji pakietu npm, [ zobaczpackage.jskonfiguracji](../javascript/configure-packages-with-package-json.md).
