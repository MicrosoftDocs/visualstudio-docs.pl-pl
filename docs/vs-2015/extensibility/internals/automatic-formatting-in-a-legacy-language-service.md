---
title: Automatyczne formatowanie w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801935"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatowanie automatyczne w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Automatyczne formatowanie usługi językowej automatycznie wstawia fragment kodu po użytkownik rozpoczyna wpisz konstrukcję kodu znane.  
  
## <a name="automatic-formatting-behavior"></a>Zachowanie automatyczne formatowanie  
 Na przykład podczas wpisywania `if`, usługa językowa automatycznie wstawi pasujące nawiasy klamrowe, lub jeśli naciśniesz klawisz ENTER, usługa językowa wymusza punkt wstawiania w nowym wierszu poziomu właściwe wcięcia w zależności od tego, czy poprzednie wiersz otwiera nowy zakres.  
  
 Filtr polecenia używana w pozostałej części usługi językowej można również automatycznego formatowania. Można również wyróżnić pasujące nawiasy klamrowe, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
