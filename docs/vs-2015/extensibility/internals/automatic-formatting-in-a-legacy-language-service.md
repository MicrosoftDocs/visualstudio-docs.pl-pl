---
title: Automatyczne formatowanie w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157270"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatowanie automatyczne w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W przypadku automatycznego formatowania usługa języka automatycznie wstawia fragment kodu, gdy użytkownik rozpocznie wpisywanie znanej konstrukcji kodu.  
  
## <a name="automatic-formatting-behavior"></a>Zachowanie automatycznego formatowania  
 Na przykład podczas wpisywania `if` Usługa językowa automatycznie wstawia pasujące nawiasy klamrowe lub naciśnięcie klawisza ENTER spowoduje wymuszenie punktu wstawiania w nowym wierszu do odpowiedniego poziomu wcięcia, w zależności od tego, czy poprzedni wiersz otwiera nowy zakres.  
  
 Filtr poleceń używany dla pozostałej części usługi językowej może być również używany do automatycznego formatowania. Możesz również wyróżnić pasujące nawiasy klamrowe, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
