---
title: Kompilowanie i kompilowanie kodu TypeScript przy użyciu narzędzia npm
description: Dowiedz się, jak dodać obsługę języka Typescript do projektów Visual Studio przy użyciu narzędzia Node Menedżer pakietów (npm).
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 96e5689c0108231be26ddf7d598227137f7bc1f7
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433782"
---
# <a name="compile-typescript-code-nodejs"></a>Kompilowanie kodu TypeScript (Node.js)

Obsługę języka TypeScript można dodać do projektów przy użyciu TypeScript SDK, domyślnie dostępnej w instalatorze Visual Studio lub przy użyciu narzędzia npm. W przypadku projektów Visual Studio 2019 zachęcamy do korzystania z pakietu npm typeScript w celu zwiększenia przenośności na różnych platformach i w różnych środowiskach.

W ASP.NET Core zaleca się zamiast tego użycie [pakietu NuGet.](../javascript/compile-typescript-code-nuget.md)

## <a name="add-typescript-support-using-npm"></a>Dodawanie obsługi języka TypeScript przy użyciu narzędzia npm

Pakiet [npm języka TypeScript dodaje](https://www.npmjs.com/package/typescript) obsługę języka TypeScript. Gdy pakiet npm dla języka TypeScript 2.1 lub wyższego zostanie zainstalowany w projekcie, odpowiednia wersja usługi językowej TypeScript zostanie załadowana do edytora.

1. [Postępuj zgodnie z](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) instrukcjami, aby zainstalować Node.js dewelopera i środowisko Node.js uruchomieniowe.

   Aby uzyskać najprostszą integrację z aplikacją Visual Studio, utwórz projekt przy użyciu jednego z szablonów języka TypeScript Node.js, takich jak szablon Blank Node.js Web Application(Pusta aplikacja internetowa). W przeciwnym razie użyj szablonu Node.js JavaScript dołączonego do Visual Studio i postępuj zgodnie z instrukcjami w tym miejscu lub użyj projektu [Otwórz folder.](../javascript/develop-javascript-code-without-solutions-projects.md)

1. Jeśli projekt jeszcze go nie zawiera, zainstaluj pakiet [npm języka TypeScript.](https://www.npmjs.com/package/typescript)

   W Eksplorator rozwiązań (w prawym okienku) otwórz *package.jsw katalogu* głównym projektu. Wymienione pakiety odpowiadają pakietom w węźle npm w Eksplorator rozwiązań. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami npm.](../javascript/npm-package-management.md)

   W przypadku Node.js można zainstalować pakiet npm języka TypeScript przy użyciu wiersza polecenia lub środowiska IDE. Aby zainstalować przy użyciu środowiska IDE, kliknij prawym przyciskiem myszy węzeł npm w programie Eksplorator rozwiązań, wybierz polecenie Zainstaluj nowy **pakiet npm,** wyszukaj język **TypeScript** i zainstaluj pakiet.

   Sprawdź opcję **npm** w oknie **Dane wyjściowe,** aby zobaczyć postęp instalacji pakietu. Zainstalowany pakiet jest wyświetlany w **węźle npm** w Eksplorator rozwiązań.

1. Jeśli projekt jeszcze go nie zawiera, dodaj plik *tsconfig* do katalogu głównego projektu. Aby dodać plik, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie Dodaj > **nowy element**. Wybierz plik **konfiguracji TypeScript JSON,** a następnie kliknij przycisk **Dodaj**.

   Visual Studio dodajetsconfig.js *pliku* do katalogu głównego projektu. Ten plik umożliwia [skonfigurowanie opcji](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora języka TypeScript.

1. Otwórz *tsconfig.jsi* zaktualizuj, aby ustawić opcje kompilatora.

   Poniżej przedstawiono przykład prostegotsconfig.js *pliku.*

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   W tym przykładzie:
   - *Funkcja include* informuje kompilator, gdzie można znaleźć pliki TypeScript (*.ts).
   - *Opcja outDir* określa folder wyjściowy dla zwykłych plików JavaScript, które są transpilowane przez kompilator języka TypeScript.
   - *Opcja sourceMap* wskazuje, czy kompilator generuje *pliki sourceMap.*

   Poprzednia konfiguracja zawiera tylko podstawowe wprowadzenie do konfigurowania języka TypeScript. Aby uzyskać informacje na temat innych opcji, zobacz [tsconfig.jsna stronie](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Kompilowanie aplikacji

1. Dodaj pliki TypeScript (*ts*) lub TypeScript JSX (*tsx*) do projektu, a następnie dodaj kod TypeScript. W przypadku prostego przykładu języka TypeScript użyj następującego kodu:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. W *package.jsw programie* dodaj obsługę poleceń Visual Studio kompilacji i czyszczenia przy użyciu następujących skryptów.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Jeśli musisz skompilować przy użyciu narzędzia innej firmy, takiego jak pakiet webpack, możesz dodać skrypt kompilacji wiersza polecenia do pliku *package.jspliku:*

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Aby uzyskać przykład użycia pakietów webpack z platformą React i plikiem konfiguracji pakietów internetowych, zobacz Tworzenie aplikacji internetowej przy [użyciu oprogramowania Node.js React.](../javascript/tutorial-nodejs-with-react-and-jsx.md)

   Aby uzyskać przykład użycia języka Vue.js typeScript, zobacz [Tworzenie Vue.js aplikacji](/javascript/create-application-with-vuejs).

1. Jeśli musisz skonfigurować opcje, takie jak strona startowa, ścieżka do środowiska uruchomieniowego programu Node.js, portu aplikacji lub argumentów środowiska uruchomieniowego, kliknij prawym przyciskiem myszy węzeł projektu w programie Eksplorator rozwiązań i wybierz polecenie Właściwości **.**

   >[!NOTE]
   > Podczas konfigurowania narzędzi innych firm projekty Node.js nie używają ścieżek skonfigurowanych w obszarze Narzędzia Opcje Projekty i rozwiązania Web  >    >    >  **Zarządzanie pakietami**  >  **zewnętrzne narzędzia sieci Web.** Te ustawienia są używane dla innych typów projektów.

1. Wybierz **pozycję > kompilacji.**

   Mimo że aplikacja jest kompilowana automatycznie po uruchomieniu, chcemy przyjrzeć się coś, co dzieje się podczas procesu kompilacji:

   Jeśli wygenerowano mapy źródłowe, otwórz folder określony w opcji *outDir* i znajdź wygenerowane pliki.js oraz wygenerowane pliki \* \* js.map.

   Źródłowe pliki mapy są wymagane do [debugowania](../javascript/debug-nodejs.md).

### <a name="run-the-application"></a>Uruchamianie aplikacji

Aby uzyskać instrukcje dotyczące uruchamiania aplikacji po jej skompilowaniu, zobacz [Tworzenie pierwszej Node.js aplikacji.](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app)

## <a name="automate-build-tasks"></a>Automatyzowanie zadań kompilacji

Eksploratora programu Task Runner w programie Visual Studio, aby ułatwić automatyzację zadań dla narzędzi innych firm, takich jak npm i webpack.

- [NpM Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) — dodaje obsługę skryptów npm zdefiniowanych wpackage.js *w programie*. Obsługuje yarn.
- [Webpack Task Runner —](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) dodaje obsługę pakietów webpack.
