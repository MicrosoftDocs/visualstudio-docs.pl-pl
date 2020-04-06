---
title: Kreator (. Vsz) Plik | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703310"
---
# <a name="wizard-vsz-file"></a>Kreator (plik Vsz)

Zintegrowane środowisko programistyczne (IDE) używa plików vsz do uruchamiania kreatorów. Te pliki vsz zawierają informacje używane przez IDE do określenia, który kreator ma wywołać i jakie informacje przekazać do kreatora.

Plik .vsz jest wersją pliku tekstowego w formacie .ini, który nie ma sekcji. Informacje znane IDE są przechowywane na początku pliku. Zapewnia to łącze między kreatora, który wywołuje IDE i parametry, które znajdują się w pliku vsz, które mają być przekazywane do IDE. Pozostała część pliku zawiera parametry, które są specyficzne dla kreatora i które mają być zbierane przez IDE i przekazywane do określonego kreatora.

W poniższym przykładzie przedstawiono zawartość pliku .vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Poniżej znajdują się części w pliku .vsz.

|Część|Opis|
|----------|-----------------|
|VsWizard (|Pierwszym parametrem w pliku jest numer wersji formatu pliku szablonu. Ten numer wersji musi być 6.0, 7.0, 7.1 lub 8.0. Nie można uruchomić innych numerów i spowodować błąd nieprawidłowego formatu.|
|Kreatora|To pole zawiera identyfikator OLE kreatora lub alternatywnie reprezentację ciągu GUID identyfikatora CLSID kreatora współtworzonego przez IDE.|
|Param|Te części są opcjonalne. Możesz dodać dowolną liczbę.|

Parametry umożliwiają plikowi vsz przekazywanie dodatkowych parametrów niestandardowych do kreatora. Każda wartość jest przekazywana jako element ciągu w tablicy wariantów do kreatora. Aby uzyskać więcej informacji, zobacz [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

Aby dodać domyślny identyfikator ustawień regionalnych do `FALLBACK_LCID`pliku vsz, określ =xxxx, gdzie xxxx jest identyfikatorem ustawień regionalnych, na przykład 1033 dla języka angielskiego. Po `FALLBACK_LCID` zdefiniowaniu parametru kreator używa podanego identyfikatora ustawień regionalnych rezerwowych, jeśli nie zostanie znaleziony bieżący identyfikator.

## <a name="see-also"></a>Zobacz też

- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
