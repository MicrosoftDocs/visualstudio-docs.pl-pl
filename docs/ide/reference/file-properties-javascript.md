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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68926235"
---
# <a name="file-properties-javascript"></a>Właściwości pliku, JavaScript

Właściwości pliku można użyć, aby wskazać, jakie akcje powinien wykonać system projektu na plikach. Na przykład można ustawić właściwości pliku, aby wskazać, czy plik ma zostać dodany do pakietu jako plik zasobów.

Możesz wybrać dowolny plik w Eksplorator rozwiązań a następnie przejrzeć jego właściwości w okno Właściwości. Pliki JavaScript mają cztery właściwości: **Kopiuj do katalogu wyjściowego**, **akcji pakietu**, **nazwy pliku**i **ścieżki pliku**.

## <a name="file-properties"></a>Właściwości pliku
W tej sekcji opisano właściwości typowe dla plików JavaScript.

### <a name="copy-to-output-directory-property"></a>Kopiuj do właściwości katalogu wyjściowego
Ta właściwość określa warunki, w których wybrany plik źródłowy zostanie skopiowany do katalogu wyjściowego. Wybierz opcję nie **Kopiuj** , jeśli plik nigdy nie będzie kopiowany do katalogu wyjściowego. Wybierz opcję **Kopiuj zawsze** , jeśli plik jest zawsze kopiowany do katalogu wyjściowego. Wybierz opcję **Kopiuj, jeśli nowszy** , jeśli plik ma być kopiowany tylko wtedy, gdy jest on nowszy niż istniejący plik o tej samej nazwie w katalogu wyjściowym.

### <a name="package-action"></a>Akcja pakietu
Właściwość **Akcja pakietu** wskazuje, co program Visual Studio wykonuje wraz z plikiem, gdy kompilacja jest wykonywana. **Akcja pakietu** może mieć jedną z kilku wartości:

- **Brak** — plik nie jest uwzględniony w manifeście pakietu. Przykładem jest plik tekstowy, który zawiera dokumentację, taką jak plik Readme.

- **Zawartość** — plik zostanie uwzględniony w manifeście pakietu. Na przykład to ustawienie jest wartością domyślną dla pliku htm, js, CSS, obrazu, audio lub wideo.

- **Manifest** — plik nie jest uwzględniony w manifeście pakietu. Zamiast tego plik jest używany do wprowadzania danych podczas generowania manifestu pakietu. Jest to wartość domyślna dla pliku Package. appxmanifest.

- **Zasób** — plik nie jest uwzględniony w manifeście pakietu. Zamiast tego zawartość pliku jest indeksowana w indeksie zasobów pakietu (PRI), który jest przekazywany do manifestu pakietu. Jest zazwyczaj używany w przypadku plików zasobów.

Wartość domyślna dla **akcji pakietu** zależy od rozszerzenia pliku dodawanego do rozwiązania.

### <a name="file-name-property"></a>Właściwość nazwy pliku
Wyświetla nazwę pliku jako wartość tylko do odczytu. Aby zmienić nazwę pliku, należy kliknąć prawym przyciskiem myszy w Eksplorator rozwiązań i wybrać polecenie **Zmień nazwę**.

### <a name="full-path-property"></a>Właściwość pełnej ścieżki
Wyświetla pełną ścieżkę do pliku jako wartość tylko do odczytu. Aby zmienić ścieżkę pliku, można przeciągnąć i upuścić plik w Eksplorator rozwiązań.

## <a name="reference-file-properties"></a>Właściwości pliku referencyjnego
W tej sekcji opisano właściwości typowe dla plików, do których odwołuje się aplikacja platformy UWP skompilowana przy użyciu języka JavaScript. Po wybraniu odwołania, takiego jak plik winmd, odwołanie do zestawu SDK, odwołanie projekt-do-projektu lub odwołanie do zestawu w Eksplorator rozwiązań, inne właściwości mogą być wyświetlane w okno Właściwości, zgodnie z typem pliku.

### <a name="culture"></a>Kultura
Wyświetla język skojarzony z odwołaniem.

### <a name="file-type"></a>Typ pliku
Wyświetla typ pliku odwołania.

### <a name="file-version"></a>Wersja pliku
Wyświetla wersję pliku odwołania.

### <a name="identity"></a>Tożsamość
Wyświetla tożsamość odwołania, która jest używana w projekcie, który jest przechowywany w pliku projektu.

### <a name="package"></a>Pakiet
Wyświetla nazwę manifestu pakietu skojarzonego z odwołaniem.

### <a name="resolved-path"></a>Rozwiązany ścieżka
Wyświetla ścieżkę do odwołania, które jest używane w projekcie.

### <a name="sdk-path"></a>Ścieżka zestawu SDK
Wyświetla ścieżkę do pliku zestawu SDK, do którego istnieje odwołanie.

### <a name="uri"></a>Adresu
Wyświetla identyfikator URI, który musi być uwzględniony w plikach HTML lub JavaScript projektu, aby dołączyć plik jako plik źródłowy.

### <a name="version"></a>Wersja
Wyświetla wersję odwołania.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie właściwościami projektów i rozwiązań](../../ide/managing-project-and-solution-properties.md)