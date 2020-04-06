---
title: Automatyczne formatowanie w starszej usłudze językowej | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709977"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatyczne formatowanie w starszej usłudze językowej
W przypadku automatycznego formatowania usługa języka automatycznie wstawia fragment kodu, gdy użytkownik zaczyna wpisywać znaną konstrukcję kodu.

## <a name="automatic-formatting-behavior"></a>Automatyczne formatowanie
 Na przykład po *wpisaniu, jeśli*usługa językowa automatycznie wstawia pasujące nawiasy klamrowe lub po naciśnięciu klawisza ENTER, usługa języka wymusza punkt wstawiania w nowym wierszu na odpowiednim poziomie wcięcia, w zależności od tego, czy poprzednia linia otwiera nowy zakres.

 Filtr poleceń używany w pozostałej części usługi językowej może być również używany do automatycznego formatowania. Można również wyróżnić pasujące <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>nawiasy klamrowe, wywołując .

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
