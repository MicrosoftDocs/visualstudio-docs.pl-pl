---
title: Automatyczne formatowanie w starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się więcej o automatycznym formatowaniu w starszej wersji usługi językowej, która automatycznie wstawia fragment kodu po rozpoczęciu wpisywania znanej konstrukcji kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de54f43ca8abc7547609882647e014cb3695da33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906056"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatyczne formatowanie w starszej wersji usługi językowej
W przypadku automatycznego formatowania usługa języka automatycznie wstawia fragment kodu, gdy użytkownik rozpocznie wpisywanie znanej konstrukcji kodu.

## <a name="automatic-formatting-behavior"></a>Zachowanie automatycznego formatowania
 Na przykład *podczas wpisywania, gdy usługa* językowa automatycznie wstawia pasujące nawiasy klamrowe lub naciśnięcie klawisza ENTER, usługa języka wymusza punkt wstawiania w nowym wierszu do odpowiedniego poziomu wcięcia, w zależności od tego, czy poprzedni wiersz otwiera nowy zakres.

 Filtr poleceń używany dla pozostałej części usługi językowej może być również używany do automatycznego formatowania. Możesz również wyróżnić pasujące nawiasy klamrowe, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Zobacz też
- [Opracowywanie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
