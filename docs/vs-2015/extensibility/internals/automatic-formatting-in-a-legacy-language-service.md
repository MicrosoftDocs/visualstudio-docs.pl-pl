---
title: Automatyczne formatowanie w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1e9be96038334edeb9163c15d16a98999bd0c2e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795495"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatowanie automatyczne w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Automatyczne formatowanie usługi językowej automatycznie wstawia fragment kodu po użytkownik rozpoczyna wpisz konstrukcję kodu znane.  
  
## <a name="automatic-formatting-behavior"></a>Zachowanie automatyczne formatowanie  
 Na przykład podczas wpisywania `if`, usługa językowa automatycznie wstawi pasujące nawiasy klamrowe, lub jeśli naciśniesz klawisz ENTER, usługa językowa wymusza punkt wstawiania w nowym wierszu poziomu właściwe wcięcia w zależności od tego, czy poprzednie wiersz otwiera nowy zakres.  
  
 Filtr polecenia używana w pozostałej części usługi językowej można również automatycznego formatowania. Można również wyróżnić pasujące nawiasy klamrowe, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

