---
title: Konfigurowanie pakietów npm przy użyciu package.jsna
description: Określ wersje pakietów npm przy użyciu package.jsna
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 652ff7b0380fc03a3f9c8155a2f8696d9dfee5b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692377"
---
# <a name="packagejson-configuration"></a>Konfiguracja pliku package.json

Jeśli tworzysz aplikację Node.jsową z wieloma pakietami npm, nie zdarza się, że występują ostrzeżenia lub błędy podczas kompilowania projektu, jeśli co najmniej jeden pakiet został zaktualizowany. Czasami wyniki konfliktów wersji lub wersja pakietu zostały wycofane. Poniżej przedstawiono kilka szybkich porad ułatwiających skonfigurowanie [package.jsw](https://docs.npmjs.com/files/package.json) pliku i zrozumienie, co się dzieje w przypadku wyświetlenia ostrzeżeń lub błędów. Nie jest to kompletny przewodnik dotyczący *package.jsw systemie* i jest skoncentrowany tylko na wersji pakietu npm.

System przechowywania wersji pakietu npm ma rygorystyczne reguły. Format wersji jest następujący:

```
[major].[minor].[patch]
```

Załóżmy, że masz pakiet w aplikacji z wersją 5.2.1. Wersja główna to 5, wersja pomocnicza to 2, a poprawka to 1.

* W ramach aktualizacji wersji głównej pakiet zawiera nowe funkcje, które są wstecznie niezgodne, czyli istotne zmiany.
* W dodatkowej wersji aktualizacji dodano nowe funkcje do pakietu, które są wstecznie zgodne ze starszymi wersjami pakietu.
* W aktualizacji poprawki uwzględniono co najmniej jedną poprawkę błędu. Poprawki błędów są zawsze zgodne z poprzednimi wersjami.

Warto zauważyć, że niektóre funkcje pakietu npm mają zależności. Na przykład aby użyć nowej funkcji pakietu kompilatora języka TypeScript (TS-Loader) z pakietem WebPack, możliwe jest również zaktualizowanie pakietu WebPack npm oraz pakietu WebPack interfejsu wiersza polecenia.

Aby ułatwić Zarządzanie wersjami pakietów, npm obsługuje kilka notacji, których można użyć w *package.jsna*. Za pomocą tych notacji można kontrolować typ aktualizacji pakietu, które mają zostać zaakceptowane w aplikacji.

Załóżmy, że korzystasz **z reakcji** i musisz dołączyć pakiet renpm i **reaguje — dom** . Można określić, że na kilka sposobów w *package.js* pliku. Na przykład można określić użycie dokładnej wersji pakietu w następujący sposób.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Korzystając z powyższej notacji, npm będzie zawsze mieć dokładną określoną wersję, 16.4.2.

Można użyć notacji specjalnej, aby ograniczyć aktualizacje aktualizacji poprawek (poprawki błędów). W tym przykładzie:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

używasz znaku tyldy (~) do informowania npm o zaktualizowaniu pakietu tylko wtedy, gdy jest on poprawiony. W związku z tym npm może aktualizować 16.4.2 do 16.4.3 (lub 16.4.4 itp.), ale nie akceptuje aktualizacji wersji głównej ani pomocniczej. W związku z tym 16.4.2 nie zostanie zaktualizowany do 16.5.0.

Można również użyć symbolu karetki (^), aby określić, że npm może zaktualizować numer wersji pomocniczej.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Korzystając z tej notacji, npm może aktualizować 16.4.2 do 16.5.0 (lub 16.5.1, 16.6.0 itp.), ale nie akceptuje aktualizacji wersji głównej. W związku z tym 16.4.2 nie zostanie zaktualizowany do 17.0.0.

Gdy npm aktualizuje pakiety, generuje *package-lock.jsw* pliku, który zawiera listę rzeczywistych wersji pakietów npm używanych w aplikacji, w tym wszystkich pakietów zagnieżdżonych. Mimo że *package.js* kontroluje bezpośrednie zależności aplikacji, nie kontroluje zagnieżdżonych zależności (innych pakietów npm wymaganych przez określony pakiet npm). Jeśli chcesz mieć pewność, że inni deweloperzy i testerzy korzystają z konkretnych używanych pakietów, w tym pakietów zagnieżdżonych, możesz użyć *package-lock.jsw* pliku w cyklu programowania. Aby uzyskać więcej informacji, zobacz [package-lock.js](https://docs.npmjs.com/files/package-lock.json) w dokumentacji npm.

W przypadku programu Visual Studio *package-lock.jsw* pliku nie jest dodawany do projektu, ale można go znaleźć w folderze projektu.
