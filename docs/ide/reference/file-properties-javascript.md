---
title: Właściwości pliku, JavaScript
ms.date: 06/21/2017
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c8bb8bc743aea29219edc8db9c0c52bf839954a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790651"
---
# <a name="file-properties-javascript"></a>Właściwości pliku, JavaScript
Aby wskazać, jakie akcje, system projektu należy wykonać na plikach, można użyć właściwości pliku. Na przykład można ustawić właściwości pliku, aby wskazać, czy plik należy dodać do pakietu jako plik zasobów.

 Można wybrać dowolny plik w Eksploratorze rozwiązań i następnie sprawdź jego właściwości w oknie dialogowym właściwości. Pliki JavaScript ma cztery właściwości: **Kopiuj do katalogu wyjściowego**, **pakietu akcji**, **nazwa pliku**, i **ścieżki pliku**.

## <a name="file-properties"></a>Właściwości pliku
 W tej sekcji opisano właściwości wspólne dla plików JavaScript.

### <a name="copy-to-output-directory-property"></a>Skopiuj do właściwości katalogu danych wyjściowych
 Ta właściwość określa warunki, w których wybranym pliku źródłowym zostaną skopiowane do katalogu wyjściowego. Wybierz **nie Kopiuj** Jeśli plik nigdy nie ma zostać skopiowany do katalogu wyjściowego. Wybierz **zawsze Kopiuj** Jeśli plik jest zawsze był kopiowany do katalogu wyjściowego. Wybierz **Kopiuj Jeśli nowszy** Jeśli plik jest kopiowany, tylko wtedy, gdy jest nowsza niż istniejący plik o takiej samej nazwie w katalogu wyjściowym.

### <a name="package-action"></a>Akcja pakietu
 **Akcja pakietu** właściwość wskazuje co program Visual Studio przy użyciu pliku po wykonaniu kompilacji. **Pakiet akcji** może mieć jeden z kilku wartości:

- **Brak** — plik nie jest uwzględniony w manifeście pakietu. Przykładem jest plik tekstowy, który zawiera dokumentację, takich jak plik Readme.

- **Zawartość** — plik jest uwzględniony w manifeście pakietu. Na przykład to ustawienie jest wartością domyślną dla .htm, js, CSS, obrazów, plików audio i wideo.

- **Manifest** — plik nie jest uwzględniony w manifeście pakietu. Zamiast tego pliku jest używany dla danych wejściowych podczas generowania manifestu pakietu. Jest to wartość domyślna dla pliku package.appxmanifest.

- **Zasób** — plik nie jest uwzględniony w manifeście pakietu. Zamiast tego należy zawartość pliku są indeksowane w indeksie zasobów pakietu (PRI), prowadzące do manifestu pakietu. Zazwyczaj służy do plików zasobów.

Wartością domyślną dla **Akcja pakietu** zależy od rozszerzenia pliku, który można dodać do rozwiązania.

### <a name="file-name-property"></a>Właściwość Nazwa pliku
 Wyświetla nazwę pliku jako wartość tylko do odczytu. Aby zmienić nazwę pliku, należy kliknąć prawym przyciskiem myszy w Eksploratorze rozwiązań i wybrać **Zmień nazwę**.

### <a name="full-path-property"></a>Pełna ścieżka właściwości
 Wyświetla pełną ścieżkę do pliku jako wartość tylko do odczytu. Aby zmienić ścieżkę pliku, możesz przeciąganie i upuszczanie plików w Eksploratorze rozwiązań.

## <a name="reference-file-properties"></a>Właściwości odwołania do pliku
 W tej sekcji opisano właściwości wspólne dla plików odwołanie z aplikacji platformy UWP skompilowane przy użyciu języka JavaScript. Po wybraniu odwołania, takich jak plik winmd, odwołanie do zestawu SDK, odwołanie projektu do projektu lub odwołanie do zestawu w Eksploratorze rozwiązań, inne właściwości mogą być wyświetlane w oknie dialogowym właściwości zgodnie z typem pliku.

### <a name="culture"></a>Kultura
 Wyświetla język skojarzonej z odwołaniem.

### <a name="file-type"></a>Typ pliku
 Wyświetla typ pliku odwołania.

### <a name="file-version"></a>Wersja pliku
 Wyświetla wersję pliku odwołania.

### <a name="identity"></a>Tożsamość
 Wyświetla tożsamość odwołania, który jest używany w projekcie, który jest przechowywany w pliku projektu.

### <a name="package"></a>Package
 Wyświetla nazwę skojarzonej z odwołaniem manifestu pakietu.

### <a name="resolved-path"></a>Rozpoznana ścieżka
 Wyświetla ścieżkę do odwołania, który jest używany w projekcie.

### <a name="sdk-path"></a>Ścieżka zestawu SDK
 Wyświetla ścieżkę do pliku zestawu SDK.

### <a name="uri"></a>Identyfikator URI
 Wyświetla identyfikator URI, który muszą być zawarte w plikach HTML i JavaScript projektu Aby dołączyć plik jako plik źródłowy.

### <a name="version"></a>Wersja
 Wyświetla wersję odwołania.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie właściwościami projektu i rozwiązania](../../ide/managing-project-and-solution-properties.md)