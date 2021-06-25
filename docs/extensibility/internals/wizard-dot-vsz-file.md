---
title: Kreator (. Vsz) Plik | Microsoft Docs
description: Dowiedz się więcej o plikach vsz, których idee używa do uruchamiania kreatorów. Pliki zawierają informacje o kreatorze do wywołania i o tym, co należy przekazać do kreatora.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de687dae79fa1613090fb400f73ab658ee5d66cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900658"
---
# <a name="wizard-vsz-file"></a>Kreator (plik Vsz)

Zintegrowane środowisko projektowe (IDE) używa plików vsz do uruchamiania kreatorów. Te pliki .vsz zawierają informacje używane przez ideę do określenia, który kreator ma wywołać i jakie informacje przekazać do kreatora.

Plik vsz to wersja pliku tekstowego .ini formatem, który nie zawiera sekcji. Informacje znane ideom są przechowywane na początku pliku. Zapewnia to połączenie między kreatorem, który wywołuje ide, a parametrami, które znajdują się w pliku vsz, które mają zostać przekazane do środowiska IDE. Pozostała część pliku zawiera parametry specyficzne dla kreatora, które mają być zbierane przez ideę IDE i przekazywane do określonego kreatora.

W poniższym przykładzie pokazano zawartość pliku vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Poniżej przedstawiono części w pliku vsz.

|Część|Opis|
|----------|-----------------|
|VsWizard|Pierwszym parametrem w pliku jest numer wersji formatu pliku szablonu. Ten numer wersji musi mieć wersję 6.0, 7.0, 7.1 lub 8.0. Nie można rozpocząć innych liczb i spowodować błędu Nieprawidłowy format.|
|Kreatora|To pole zawiera identyfikator OLE ProgID kreatora lub alternatywnie ciąg identyfikatora GUID reprezentacji identyfikatora CLSID kreatora, który jest współtworzyny przez ideę.|
|Param|Te części są opcjonalne. Możesz dodać tyle, ile potrzebujesz.|

Parametry umożliwiają plikowi vsz przekazania dodatkowych parametrów niestandardowych do kreatora. Każda wartość jest przekazywana do kreatora jako element ciągu w tablicy wariantów. Aby uzyskać więcej informacji, zobacz [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

Aby dodać domyślny identyfikator ustawień regionalnych do pliku vsz, określ wartość =xxxx, gdzie xxxx to identyfikator ustawień regionalnych, na przykład `FALLBACK_LCID` 1033 dla języka angielskiego. Gdy `FALLBACK_LCID` parametr jest zdefiniowany, kreator używa podanego identyfikatora rezerwowych ustawień regionalnych, jeśli bieżący identyfikator nie zostanie znaleziony.

## <a name="see-also"></a>Zobacz też

- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
