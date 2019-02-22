---
title: Automatyczne formatowanie w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64fbf5b64b57425b1bdee3ae3475c234384db062
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626157"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatowanie automatyczne w starszej wersji usługi językowej
Automatyczne formatowanie usługi językowej automatycznie wstawia fragment kodu po użytkownik rozpoczyna wpisz konstrukcję kodu znane.

## <a name="automatic-formatting-behavior"></a>Zachowanie automatyczne formatowanie
 Na przykład podczas wpisywania *Jeśli*, usługa językowa automatycznie wstawi pasujące nawiasy klamrowe, lub jeśli naciśniesz klawisz ENTER, usługa językowa wymusza punkt wstawiania w nowym wierszu poziomu właściwe wcięcia, w zależności od czy poprzedni wiersz otwiera nowy zakres.

 Filtr polecenia używana w pozostałej części usługi językowej można również automatycznego formatowania. Można również wyróżnić pasujące nawiasy klamrowe, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.

## <a name="see-also"></a>Zobacz także
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)