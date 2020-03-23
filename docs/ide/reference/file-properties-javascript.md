---
title: Właściwości pliku, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b27f103b2431914efbd22c119e11221b5814dae4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926235"
---
# <a name="file-properties-javascript"></a>Właściwości pliku, JavaScript

Właściwości pliku można użyć, aby wskazać, jakie akcje system projektu powinien wykonać na plikach. Na przykład można ustawić właściwości pliku, aby wskazać, czy plik powinien zostać dodany do pakietu jako plik zasobu.

Można wybrać dowolny plik w Eksploratorze rozwiązań, a następnie sprawdzić jego właściwości w oknie Właściwości. Pliki JavaScript mają cztery właściwości: **Kopiuj do katalogu wyjściowego,** **Akcja pakietu,** **Nazwa pliku**i **Ścieżka pliku.**

## <a name="file-properties"></a>Właściwości pliku
W tej sekcji opisano właściwości typowe dla plików JavaScript.

### <a name="copy-to-output-directory-property"></a>Właściwość Kopiowanie do katalogu wyjściowego
Ta właściwość określa warunki, w których wybrany plik źródłowy zostanie skopiowany do katalogu wyjściowego. Wybierz **opcję Nie kopiuj,** jeśli plik nigdy nie ma być kopiowany do katalogu wyjściowego. Wybierz **opcję Kopiuj zawsze,** jeśli plik ma być zawsze kopiowany do katalogu wyjściowego. Wybierz **opcję Kopiuj, jeśli** plik ma być kopiowany tylko wtedy, gdy jest nowszy niż istniejący plik o tej samej nazwie w katalogu wyjściowym.

### <a name="package-action"></a>Akcja pakietu
Właściwość **akcja pakietu** wskazuje, co program Visual Studio robi z plikiem podczas wykonywania kompilacji. **Akcja pakietu** może mieć jedną z kilku wartości:

- **Brak** — plik nie jest uwzględniony w manifeście pakietu. Przykładem jest plik tekstowy zawierający dokumentację, taką jak plik Readme.

- **Zawartość** — plik znajduje się w manifeście pakietu. Na przykład to ustawienie jest wartością domyślną dla pliku .htm, .js, css, image, audio lub wideo.

- **Manifest** — plik nie jest uwzględniony w manifeście pakietu. Zamiast tego plik jest używany do wprowadzania danych podczas generowania manifestu pakietu. Jest to wartość domyślna dla pliku package.appxmanifest.

- **Zasób** — plik nie jest uwzględniony w manifeście pakietu. Zamiast tego zawartość pliku są indeksowane w indeksie zasobów pakietu (PRI), który przechodzi do manifestu pakietu. Zazwyczaj jest używany dla plików zasobów.

Wartość domyślna **dla akcji pakietu** zależy od rozszerzenia pliku, który można dodać do rozwiązania.

### <a name="file-name-property"></a>Właściwość nazwa pliku
Wyświetla nazwę pliku jako wartość tylko do odczytu. Aby zmienić nazwę pliku, należy kliknąć prawym przyciskiem myszy w Eksploratorze rozwiązań i wybrać **polecenie Zmień nazwę**.

### <a name="full-path-property"></a>Pełna właściwość path
Wyświetla pełną ścieżkę do pliku jako wartość tylko do odczytu. Aby zmienić ścieżkę pliku, można przeciągnąć i upuścić plik w Eksploratorze rozwiązań.

## <a name="reference-file-properties"></a>Właściwości pliku odwołań
W tej sekcji opisano właściwości typowe dla plików, do których odwołuje się aplikacja platformy uniwersalnej systemuśpiłna schyłana przy użyciu języka JavaScript. Po wybraniu odwołania, takiego jak plik .winmd, odwołanie do zestawu SDK, odwołanie do projektu lub odwołanie do zestawu w Eksploratorze rozwiązań, inne właściwości mogą być wyświetlane w oknie Właściwości, zgodnie z typem pliku.

### <a name="culture"></a>Culture
Wyświetla język skojarzony z odwołaniem.

### <a name="file-type"></a>Typ pliku
Wyświetla typ pliku odwołania.

### <a name="file-version"></a>Wersja pliku
Wyświetla wersję pliku odwołania.

### <a name="identity"></a>Tożsamość
Wyświetla tożsamość odwołania, który jest używany w projekcie, który jest przechowywany w pliku projektu.

### <a name="package"></a>Pakiet
Wyświetla nazwę manifestu pakietu skojarzonego z odwołaniem.

### <a name="resolved-path"></a>Rozwiązana ścieżka
Wyświetla ścieżkę do odwołania, który jest używany w projekcie.

### <a name="sdk-path"></a>Ścieżka SDK
Wyświetla ścieżkę do pliku SDK, do którego istnieje odwołanie.

### <a name="uri"></a>Identyfikator uri
Wyświetla identyfikator URI, który musi zostać uwzględniony w plikach HTML lub JavaScript projektu, aby uwzględnić plik jako plik źródłowy.

### <a name="version"></a>Wersja
Wyświetla wersję odwołania.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie właściwościami projektów i rozwiązań](../../ide/managing-project-and-solution-properties.md)