---
title: Kompilowanie i kompilowanie kodu TypeScript przy użyciu npm
description: Dowiedz się, jak kompilować i kompilować TypeScript w programie Visual Studio.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 7d70f1e95ce2dd5163eb017684620c403a77f74a
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740035"
---
# <a name="compile-typescript-code-nodejs"></a>Kompiluj kod języka TypeScript (Node.js)

Obsługę języka TypeScript można dodać do swoich projektów przy użyciu TypeScript SDK, która jest domyślnie dostępna w Instalatorze programu Visual Studio lub za pomocą npm. W przypadku projektów utworzonych w programie Visual Studio 2019 zachęcamy do korzystania z pakietu npm języka TypeScript w celu uzyskania większej przenośności na różnych platformach i środowiskach.

W przypadku projektów ASP.NET Core zaleca się używanie [pakietu NuGet](../javascript/compile-typescript-code-nuget.md) zamiast tego.

## <a name="add-typescript-support-using-npm"></a>Dodawanie obsługi języka TypeScript przy użyciu npm

[Pakiet TypeScript npm](https://www.npmjs.com/package/typescript) dodaje obsługę języka TypeScript. Gdy pakiet npm dla języka TypeScript 2,1 lub nowszego jest instalowany w projekcie, odpowiednia wersja usługi języka TypeScript zostanie załadowana w edytorze.

1. [Postępuj zgodnie z instrukcjami](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) , aby zainstalować Node.js obciążenie programowaniem i Node.js środowiska uruchomieniowego.

   Dla najprostszej integracji z programem Visual Studio Utwórz projekt przy użyciu jednego z Node.js szablonów języka TypeScript, takich jak szablon Node.js aplikacji sieci Web. W przeciwnym razie użyj szablonu JavaScript Node.js dołączonego do programu Visual Studio i postępuj zgodnie z instrukcjami w tym miejscu lub Użyj projektu [otwartego folderu](../javascript/develop-javascript-code-without-solutions-projects.md) .

1. Jeśli projekt nie zawiera jeszcze go, zainstaluj [pakiet TypeScript npm](https://www.npmjs.com/package/typescript).

   Z Eksplorator rozwiązań (prawego okienka) Otwórz *package.jsw elemencie* głównym projektu. Wymienione pakiety odpowiadają pakietom w węźle npm w Eksplorator rozwiązań. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami npm](../javascript/npm-package-management.md).

   W przypadku projektu Node.js można zainstalować pakiet TypeScript npm przy użyciu wiersza polecenia lub środowiska IDE. Aby zainstalować program przy użyciu środowiska IDE, kliknij prawym przyciskiem myszy węzeł npm w Eksplorator rozwiązań, wybierz polecenie **Zainstaluj nowy pakiet npm**, Wyszukaj pozycję **TypeScript**i zainstaluj pakiet.

   Zaznacz opcję **npm** w oknie **danych wyjściowych** , aby wyświetlić postęp instalacji pakietu. Zainstalowany pakiet jest wyświetlany w węźle **npm** w Eksplorator rozwiązań.

1. Jeśli projekt nie zawiera jeszcze go, Dodaj plik *. tsconfig* do katalogu głównego projektu. Aby dodać plik, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **dodaj > nowy element**. Wybierz **plik konfiguracji języka TYPESCRIPT JSON**, a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje *tsconfig.js* do pliku w katalogu głównym projektu. Tego pliku można użyć do [skonfigurowania opcji](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora języka TypeScript.

1. Otwórz *tsconfig.js* i zaktualizuj, aby ustawić odpowiednie opcje kompilatora.

   Poniżej znajduje się przykład prostego *tsconfig.jsw* pliku.

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
   - *include zawiera* informacje o kompilatorze, gdzie można znaleźć pliki TypeScript (*. TS).
   - Opcja *outDir* określa folder wyjściowy dla zwykłych plików JavaScript, które są transstertne przez kompilator języka TypeScript.
   - Opcja *mapy źródła* wskazuje, czy kompilator generuje pliki *mapy źródła* .

   Poprzednia konfiguracja zawiera tylko podstawowe wprowadzenie do konfigurowania języka TypeScript. Aby uzyskać informacje o innych opcjach, zobacz [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Kompilowanie aplikacji

1. Dodaj do projektu pliki TypeScript (*. TS*) lub TypeScript JSX (*. TSX*), a następnie Dodaj kod języka TypeScript. Aby zapoznać się z prostym przykładem języka TypeScript, użyj następujących elementów:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. W *package.jsw systemie*dodano obsługę poleceń Kompiluj i oczyść programu Visual Studio przy użyciu następujących skryptów.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Jeśli konieczne jest skompilowanie przy użyciu narzędzia innej firmy, takiego jak WebPack, można dodać skrypt kompilacji wiersza polecenia do *package.jsw* pliku:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Przykład korzystania z pakietu WebPack z repliką i plikiem konfiguracji pakietu WebPack można znaleźć w temacie [Tworzenie aplikacji sieci Web przy użyciu Node.js i reagowanie](../javascript/tutorial-nodejs-with-react-and-jsx.md)na nie.

   Przykład używania Vue.js z językiem TypeScript można znaleźć w temacie [Tworzenie aplikacji Vue.js](/javascript/create-application-with-vuejs).

1. Jeśli trzeba skonfigurować opcje, takie jak Strona początkowa, ścieżka do Node.js środowiska uruchomieniowego, port aplikacji lub argumentów środowiska uruchomieniowego, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań, a następnie wybierz polecenie **Właściwości**.

   >[!NOTE]
   > Podczas konfigurowania narzędzi innych firm projekty Node.js nie używają ścieżek skonfigurowanych w obszarze **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**  >  **sieci Web zarządzanie pakietami**  >  **zewnętrznych narzędzi sieci Web**. Te ustawienia są używane dla innych typów projektów.

1. Wybierz **kompiluj > Kompiluj rozwiązanie**.

   Mimo że aplikacja automatycznie kompiluje się po uruchomieniu, chcemy obejrzeć coś, co się dzieje w trakcie procesu kompilacji:

   Jeśli zostały wygenerowane mapy źródeł, Otwórz folder określony w opcji *outDir* , a następnie Znajdź wygenerowany \* plik js wraz z wygenerowanymi \* plikami js. map.

   Pliki mapy źródłowej są wymagane do [debugowania](../javascript/debug-nodejs.md).

## <a name="automate-build-tasks"></a>Automatyzowanie zadań kompilacji

Możesz użyć Eksploratora modułu uruchamiającego zadania w programie Visual Studio, aby pomóc zautomatyzować zadania dla narzędzi innych firm, takich jak npm i WebPack.

- Moduł uruchamiający [zadania npm](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) — dodaje obsługę skryptów npm zdefiniowanych w *package.jsw systemie*. Obsługuje przędzę.
- Moduł uruchamiający [zadania pakietu WebPack](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) — dodaje obsługę pakietu WebPack.