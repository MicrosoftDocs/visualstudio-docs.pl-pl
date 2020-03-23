---
title: Konfigurowanie pakietów npm za pomocą pliku package.json
description: Określanie wersji pakietu npm przy użyciu pliku package.json
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "67692377"
---
# <a name="packagejson-configuration"></a>Konfiguracja pliku package.json

Jeśli tworzysz aplikację Node.js z dużą ilością pakietów npm, nie jest rzadkością, aby uruchomić ostrzeżenia lub błędy podczas tworzenia projektu, jeśli jeden lub więcej pakietów został zaktualizowany. Czasami wyniki konfliktu wersji lub wersja pakietu została przestarzała. Oto kilka szybkich wskazówek, które pomogą Ci skonfigurować plik [package.json](https://docs.npmjs.com/files/package.json) i zrozumieć, co się dzieje, gdy widzisz ostrzeżenia lub błędy. Nie jest to kompletny przewodnik po *package.json* i koncentruje się tylko na wersji pakietu npm.

System przechowywania wersji pakietu npm ma surowe zasady. Format wersji jest następujący:

```
[major].[minor].[patch]
```

Załóżmy, że masz pakiet w aplikacji z wersją 5.2.1. Wersja główna to 5, wersja pomocnicza to 2, a łatka to 1.

* W aktualizacji wersji głównej pakiet zawiera nowe funkcje, które są niezgodne z tyłu, czyli zmiany podziału.
* W wersji pomocniczej aktualizacja nowych funkcji zostały dodane do pakietu, które są wstecznie zgodne z wcześniejszymi wersjami pakietu.
* W aktualizacji poprawki uwzględniono co najmniej jedną poprawkę. Poprawki błędów są zawsze zgodne z powrotem.

Warto zauważyć, że niektóre funkcje pakietu npm mają zależności. Na przykład, aby użyć nowej funkcji pakietu kompilatora TypeScript (ts-loader) z pakietem internetowym, możliwe jest również, że należy zaktualizować pakiet npm webpack i pakiet webpack-cli.

Aby ułatwić zarządzanie przechowywaniem wersji pakietów, npm obsługuje kilka notacji, których można użyć w *pliku package.json*. Za pomocą tych notacji można kontrolować typ aktualizacji pakietu, które chcesz zaakceptować w aplikacji.

Załóżmy, że używasz React i trzeba uwzględnić **react** **i react-dom** npm pakietu. Można określić, że na kilka sposobów w pliku *package.json.* Na przykład można określić użycie dokładnej wersji pakietu w następujący sposób.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Korzystając z poprzedniego notacji, npm zawsze otrzyma dokładną wersję określoną, 16.4.2.

Możesz użyć specjalnego notacji, aby ograniczyć aktualizacje do aktualizacji poprawek (poprawek). W tym przykładzie:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

możesz użyć znaku tyldy (~), aby powiedzieć npm, aby aktualizował pakiet tylko wtedy, gdy jest załatany. Tak, npm może zaktualizować reagować 16.4.2 do 16.4.3 (lub 16.4.4, itp.), ale nie zaakceptuje aktualizacji do wersji głównej lub pomocniczej. Tak więc, 16.4.2 nie zostanie zaktualizowany do 16.5.0.

Można również użyć symbolu dauszy (^), aby określić, że npm może zaktualizować numer wersji pomocniczej.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Korzystając z tego notacji, npm może zaktualizować react 16.4.2 do 16.5.0 (lub 16.5.1, 16.6.0 itp.), ale nie zaakceptuje aktualizacji wersji głównej. Tak więc, 16.4.2 nie zostanie zaktualizowany do 17.0.0.

Gdy npm aktualizuje pakiety, generuje plik *package-lock.json,* który zawiera listę rzeczywistych wersji pakietu npm używanych w aplikacji, w tym wszystkich pakietów zagnieżdżonych. *Package.json* kontroluje bezpośrednie zależności aplikacji, ale nie kontroluje zagnieżdżonych zależności (innych pakietów npm wymaganych przez określony pakiet npm). Można użyć *pliku package-lock.json* w cyklu dewelopera, jeśli trzeba upewnić się, że inni deweloperzy i testerzy używają dokładnie pakietów, których używasz, w tym pakietów zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [package-lock.json](https://docs.npmjs.com/files/package-lock.json) w dokumentacji npm.

W programie Visual Studio plik *package-lock.json* nie jest dodawany do projektu, ale można go znaleźć w folderze projektu.
