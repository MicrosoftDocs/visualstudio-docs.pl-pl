---
title: 'Instrukcje: obsługa konspektu w starszej wersji usługi językowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92baa824dbb70dd591cadef99775f943c651aef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837066"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Instrukcje: obsługa zwijania w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Konspekt służy do rozwijania lub zwijania różnych regionów tekstu. Sposób użycia konspektu można zdefiniować inaczej w różnych językach. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](../../ide/outlining.md).  
  
 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji konspektu, zobacz [Przewodnik: Tworzenie konspektu](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.  
  
 Poniżej przedstawiono sposób obsługi tego polecenia dla usługi językowej.  
  
### <a name="to-support-outlining"></a>Aby obsłużyć Tworzenie konspektu  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> w obiekcie usługi językowej.  
  
2. Zadzwoń <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> do bieżącego obiektu sesji tworzenia konspektu, aby dodać nowe regiony.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Gdy użytkownik wybierze opcję **Zwiń do definicji** w menu **KONSPEKTU** , środowisko IDE wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> w usłudze językowej.  
  
 Gdy ta metoda jest wywoływana, IDE kończy się <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> wskaźnikiem (wskaźnikiem do buforu tekstowego) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (wskaźnikiem do bieżącej sesji tworzenia konspektu).  
  
 Można wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodę dla wielu regionów konspektu, określając te regiony w `rgOutlnReg` parametrze. `rgOutlnReg`Parametr jest <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> strukturą. Ten proces umożliwia określenie różnych właściwości ukrytego regionu, na przykład tego, czy określony region jest rozwinięty, czy zwinięty.  
  
> [!NOTE]
> Należy zachować ostrożność podczas ukrywania znaków nowego wiersza. Tekst ukryty powinien zostać rozbudowany od początku pierwszego wiersza do ostatniego znaku ostatniego wiersza w sekcji, pozostawiając widoczny ostatni znak w wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
