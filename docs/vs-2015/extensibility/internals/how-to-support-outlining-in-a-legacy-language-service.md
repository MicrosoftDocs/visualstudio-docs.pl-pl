---
title: 'Instrukcje: Obsługa zwijania w starszej wersji usługi językowej | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436141"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Instrukcje: Obsługa zwijania w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Konspekt jest używany do rozwinąć lub zwinąć różnych regionach tekstu. Konspekt sposób jest używany może być określony inaczej w różnych językach. Aby uzyskać więcej informacji, zobacz [konspekt](../../ide/outlining.md).  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej na temat nowy sposób, aby zaimplementować Tworzenie konspektu, zobacz [instruktażu: Konspekt](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
 Poniżej przedstawiono sposób obsługi tego polecenia dla usługi języka.  
  
### <a name="to-support-outlining"></a>Aby obsługiwać tworzenie konspektu  
  
1. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> na obiekcie usługi języka.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> dla bieżącego obiektu sesji konspektu można dodać nowe regiony konspektu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Gdy użytkownik wybierze **Zwiń do definicji** na **konspekt** menu, wywołania IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> na usługi w języka.  
  
 Gdy ta metoda jest wywoływana, IDE przekazuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> kursor (wskaźnik do buforu tekstowego) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (wskaźnik do bieżącej sesji konspektu).  
  
 Możesz wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodę dla wielu regionów konspektu, określając tych regionów w `rgOutlnReg` parametru. `rgOutlnReg` Parametr <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struktury. Ten proces pozwala określić inną charakterystykę ukryty region, np. czy rozwinięta czy zwinięta danego regionu.  
  
> [!NOTE]
> Należy zachować ostrożność ukrywanie znaki nowego wiersza. Tekst ukryty powinny rozszerzać od samego początku pierwszego wiersza do ostatniego znaku ostatni wiersz w sekcji, pozostawiając widoczne ostatni znak nowego wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
