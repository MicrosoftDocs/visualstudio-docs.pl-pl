---
title: IntelliSense Hosting | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203899"
---
# <a name="intellisense-hosting"></a>Hosting funkcji IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio umożliwia hostowanie funkcji IntelliSense. Umożliwia hostowanie IntellSense udostępni funkcję IntelliSense dla kodu, który nie jest obsługiwany przez Edytor tekstu Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Użycie obsługi technologii IntelliSense  
 W programie Visual Studio, wszelki kod, który ma dostęp do zestawu uzupełniania i buforu tekstowego można uzyskać funkcji IntelliSense w systemie windows z dowolnego miejsca w interfejsie użytkownika (UI). Niektóre przykładowe scenariusze dotyczące tego, czy uzupełnianie w **Obejrzyj** oknie lub w polu stanu w oknie Właściwości punktu przerwania.  
  
### <a name="implementation-interfaces"></a>Implementacja interfejsy  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Dowolny składnik interfejsu użytkownika, który obsługuje wyskakujące IntelliSense musi obsługiwać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu. Domyślny widok tekstu edytora core obejmuje zasobu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementacji, aby zachować bieżącą funkcjonalność IntelliSense interfejsu. W większości przypadków metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu stanowią podzbiór co to jest wdrażana w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu. Podzbiór ten obejmuje obsługi interfejsu użytkownika funkcji IntelliSense, karetki i manipulowania wybór i prosty tekst zastępczy funkcji. Ponadto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu włącza oddzielne IntelliSense "temat" i "kontekst". Dzięki temu IntelliSense może być dostarczona dla tematów, które nie istnieją bezpośrednio w buforze tekstu, który jest używany dla kontekstu.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Musi implementować interfejsu dostawcę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> obsługuje metodę, aby włączyć klienta ustalić, jakiego rodzaju IntelliSense funkcji hosta.  
  
 Flagi hosta, zdefiniowane w [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), zestawiono poniżej.  
  
|Flagi funkcji IntelliSense hosta|Opis|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Ustawienie to oznacza flagą buforu kontekstu jest tylko do odczytu i edycji występuje tylko w obrębie tekstu tematu.|  
|IHF_NOSEPERATESUBJECT|Ustawienia oznacza, że flaga nie jest Brak oddzielnych tematu IntelliSense. Temat istnieje w buforu kontekstu, takich jak w przypadku tradycyjnych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense system.|  
|IHF_SINGLELINESUBJECT|Ustawienie to oznacza flagą temat nie jest wielowierszowy możliwością, na przykład w jednym wierszu edytować w **Obejrzyj** okna.|  
|IHF_FORCECOMMITTOCONTEXT|Jeśli ta flaga jest ustawiona, muszą zostać zaktualizowane buforu kontekstu hosta umożliwia flagi tylko do odczytu dla buforu kontekstu, które mają być ignorowane i zmiany, aby kontynuować.|  
|IHF_OVERTYPE|Edytowanie (podmiotu lub w kontekście) ma się odbywać w trybie zastępowania.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit i IVsIntellisenseHost.AfterCompletorCommit  
 Te metody wywołania zwrotnego są wywoływane przez okna ukończenia, przed i po zatwierdzone, aby umożliwić przetwarzanie końcowe i wstępnego przetwarzania tekstu.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Interfejs jest nieco wspólnie tworzyć w oknie ukończenia standardowego, w którym jest używany przez zintegrowanego środowiska programistycznego (IDE). Wszelkie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu szybko można zaimplementować funkcję IntelliSense za pomocą tego interfejsu completor.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
