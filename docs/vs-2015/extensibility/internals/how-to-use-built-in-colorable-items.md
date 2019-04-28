---
title: 'Instrukcje: Używanie wbudowanych elementów z możliwością kolorowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436130"
---
# <a name="how-to-use-built-in-colorable-items"></a>Instrukcje: Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przed użyciem wbudowanych elementów z możliwością kolorowania użytkownik musi najpierw zasygnalizowania do zintegrowanego środowiska programistycznego (IDE) są one udostępniane własne niestandardowe elementy z możliwością kolorowania, w tym przypadku byłaby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> obiektów. Możesz to zrobić, ustawiając wpis rejestru dla usługi w języka.  
  
### <a name="to-use-built-in-colorable-items"></a>Aby użyć wbudowanych elementów z możliwością kolorowania  
  
1. W obszarze HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*usług \Languages\Language\\*Nazwa języka*, gdzie *X.Y* jest wersją [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i *Nazwa języka* nazywa się Twój język, utworzyć wartości wpisu rejestru DWORD o nazwie `RequestStockColors`.  
  
2. Ustaw `RequestStockColors` wartości wpisu rejestru na wartość 1.  
  
     Po utworzeniu wpisu rejestru colorizer Twojej firmy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda może używać członkowie <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> wyliczeniu, aby wypełnić tablicę atrybutów koloru do użycia przez edytor.  
  
    > [!NOTE]
    > Nie należy ustawiać ten wpis rejestru, jeśli udostępniasz niestandardowe elementy z możliwością kolorowania. Aby uzyskać więcej informacji, zobacz [niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)   
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)
