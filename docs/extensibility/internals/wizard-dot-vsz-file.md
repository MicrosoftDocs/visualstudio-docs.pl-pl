---
title: Kreator (. Plik Vsz) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1bd68e9d647f9a44eaa8b975995f2d7de3d9640
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014018"
---
# <a name="wizard-vsz-file"></a>Kreator (plik Vsz)

Zintegrowane środowisko programistyczne (IDE) korzysta z plików .vsz do uruchamiania kreatorów. Te pliki .vsz zawierają informacje, które używa środowiska IDE, aby określić które kreatora do wywołania i jakie informacje do przekazania do kreatora.

Plik .vsz jest wersja pliku tekstu w formacie pliku ini, który ma nie sekcji. Informacje znane IDE znajduje się na początku pliku. Zapewnia to łącze między kreatora, który wywołuje IDE i parametry, które znajdują się w pliku .vsz do przekazania do środowiska IDE. Pozostała część pliku zawiera parametry specyficznych dla kreatora, i które mają być zbierane przez środowisko IDE i przekazywane do określonych kreatora.

Poniższy przykład pokazuje zawartość pliku .vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Poniżej przedstawiono części w pliku .vsz.

|Część|Opis|
|----------|-----------------|
|VSWizard|Pierwszy parametr w pliku jest numer wersji formatu pliku szablonu. Numer wersji musi być w wersji 6.0, 7.0, 7.1 lub 8.0. Inne liczby nie można uruchomić i powodują wystąpienie błędu nieprawidłowy Format.|
|Kreator|To pole zawiera OLE ProgID kreatora lub też ciąg reprezentujący identyfikator GUID identyfikatora CLSID kreatora, który jest cocreated IDE.|
|Param|Te elementy są opcjonalne. Możesz dodać dowolną liczbę wymaganych.|

Parametry włączenia pliku .vsz do przekazania dodatkowych parametrów niestandardowych do kreatora. Każda wartość jest przekazywana jako element ciągu w tablicy wariantów do kreatora. Aby uzyskać więcej informacji, zobacz [parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

Aby dodać domyślny identyfikator ustawień regionalnych do pliku .vsz, określ `FALLBACK_LCID`= xxxx, gdzie xxxx to identyfikator ustawień regionalnych, na przykład 1033 dla języka angielskiego. Gdy `FALLBACK_LCID` zdefiniowano parametru, jeśli bieżący identyfikator nie zostanie znaleziony, kreator używa Identyfikatora ustawień regionalnych rezerwowego.

## <a name="see-also"></a>Zobacz także

- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)