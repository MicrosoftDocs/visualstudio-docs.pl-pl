---
title: Automatyczne formatowanie w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709977"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatyczne formatowanie w starszej wersji usługi językowej
W przypadku automatycznego formatowania usługa języka automatycznie wstawia fragment kodu, gdy użytkownik rozpocznie wpisywanie znanej konstrukcji kodu.

## <a name="automatic-formatting-behavior"></a>Zachowanie automatycznego formatowania
 Na przykład *podczas wpisywania, gdy usługa*językowa automatycznie wstawia pasujące nawiasy klamrowe lub naciśnięcie klawisza ENTER, usługa języka wymusza punkt wstawiania w nowym wierszu do odpowiedniego poziomu wcięcia, w zależności od tego, czy poprzedni wiersz otwiera nowy zakres.

 Filtr poleceń używany dla pozostałej części usługi językowej może być również używany do automatycznego formatowania. Możesz również wyróżnić pasujące nawiasy klamrowe, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Zobacz też
- [Opracowywanie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
