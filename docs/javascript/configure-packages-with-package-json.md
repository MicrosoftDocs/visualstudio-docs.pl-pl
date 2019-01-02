---
title: Konfigurowanie pakietów npm przy użyciu pliku package.json
description: Określ wersje pakietów npm przy użyciu pliku package.json
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f2712545659d66b421de78d8f8835a613563fdd0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857095"
---
# <a name="packagejson-configuration"></a>Konfiguracja pliku package.json

Jeśli tworzysz aplikację platformy Node.js z dużą liczbą pakietów npm nie jest niczym niezwykłym wystąpiły ostrzeżenia i błędy podczas kompilowania projektu, jeśli co najmniej jeden pakiet został zaktualizowany. Czasami wyniki konflikt wersji lub wersji pakietu jest przestarzała. Oto kilka szybkich porad, aby pomóc w skonfigurowaniu Twojej [package.json](https://docs.npmjs.com/files/package.json) pliku i zrozumieć, co się dzieje po wyświetleniu ostrzeżenia lub błędy. Nie jest to kompletny przewodnik dotyczący *package.json* i koncentruje się tylko na przechowywanie wersji pakietów npm.

System przechowywania wersji pakietu npm ma ścisłych zasad. Format wersji następuje tutaj:

    [major].[minor].[patch]

Załóżmy, że masz pakiet w swojej aplikacji za pomocą wersji 5.2.1. Wersja główna wynosi 5, wersja pomocnicza jest 2 i poprawka jest 1.

* W ramach aktualizacji wersji głównych pakiet zawiera nowe funkcje, które są wstecznie niezgodny, który istotne zmiany.
* Aktualizacja wersji pomocniczej, nowe funkcje zostały dodane do pakietu, które są wstecznie zgodne ze starszymi wersjami pakietu.
* W ramach aktualizacji poprawki co najmniej jeden poprawki są uwzględniane. Poprawki błędów zawsze są wstecznie zgodne.

Warto zauważyć, że niektóre funkcje pakietu npm mają zależności. Na przykład aby użyć nowej funkcji pakietu kompilatora TypeScript (modułu ładującego usług terminalowych) z webpack, jest możliwe, należy również zaktualizować pakiet npm webpack i interfejs wiersza polecenia webpack.

Aby ułatwić zarządzanie, przechowywanie wersji pakietów, npm obsługuje kilka notacji, których można używać w *package.json*. Aby kontrolować typ aktualizacji pakietu, które mają zostać zaakceptowane w swojej aplikacji, można użyć tych notacji.

Załóżmy, że używasz platformy React i musi zawierać **react** i **react-dom** pakietów Menedżera npm. Użytkownik może określić, że na kilka sposobów, w swojej *package.json* pliku. Na przykład użyj dokładną wersję pakietu można określić w następujący sposób.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Przy użyciu notacji poprzedniej, npm będą zawsze uzyskać dokładną wersję określoną, 16.4.2.

Specjalne notacji służy do ograniczania aktualizacji w celu aktualizacji poprawki (poprawki). W tym przykładzie:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

znak tyldy (~) umożliwia Poinformuj aktualizacja samego programu npm pakietu, gdy jest zastosowana poprawka. Dlatego npm można zaktualizować react 16.4.2 do 16.4.3 (lub 16.4.4, itp.), ale nie będzie akceptować aktualizację do wersji mniejszym lub większym stopniu. Dlatego 16.4.2 nie zostaną zaktualizowane, aby 16.5.0.

Można również użyć symbolu daszka (^) do określania, że ten npm można zaktualizować pomocniczy numer wersji.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Notacji, npm, można zaktualizować react 16.4.2 do 16.5.0 (lub 16.5.1, 16.6.0, itp.), ale nie będzie akceptować aktualizację do wersji głównej. Dlatego 16.4.2 nie zostaną zaktualizowane, aby 17.0.0.

Po zaktualizowaniu pakietów npm generuje *lock.json pakietu* pliku, który zawiera listę wersji pakietu npm rzeczywiste używane w aplikacji, w tym wszystkich zagnieżdżonych pakietów. Gdy *package.json* formantów zależności bezpośrednich dla aplikacji, ta funkcja nie kontroluje zagnieżdżonych zależności (inne wymagane przez pakiet npm określonego pakietów npm). Możesz użyć *lock.json pakietu* plik w cyklu rozwoju, jeśli musisz upewnić się, że inne deweloperzy i testerzy korzystają z dokładną pakiety, które są używane, łącznie z pakietów zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [lock.json pakietu](https://docs.npmjs.com/files/package-lock.json) w dokumentacji programu npm.

Dla programu Visual Studio *lock.json pakietu* plik nie zostanie dodany do projektu, ale możesz go znaleźć w folderze projektu.
