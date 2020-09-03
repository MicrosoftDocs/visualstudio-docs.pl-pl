---
title: Hosting IntelliSense | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203899"
---
# <a name="intellisense-hosting"></a>Hosting funkcji IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio umożliwia hosting funkcji IntelliSense. Hosting IntellSense umożliwia dostarczenie funkcji IntelliSense dla kodu, który nie jest obsługiwany przez Edytor tekstu programu Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Użycie funkcji IntelliSense  
 W programie Visual Studio każdy kod, który ma dostęp do zestawu uzupełniania i bufor tekstu, może uzyskać okna IntelliSense z dowolnego miejsca w interfejsie użytkownika. Niektóre przykładowe scenariusze tego są uzupełniane w oknie **czujki** lub w polu warunek okna właściwości punktu przerwania.  
  
### <a name="implementation-interfaces"></a>Interfejsy implementacji  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Każdy składnik interfejsu użytkownika, który hostuje okna podręczne IntelliSense, musi obsługiwać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejs. Domyślny widok tekstowy edytora podstawowego zawiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementację interfejsu podstawowego, która zachowuje bieżące funkcje IntelliSense. W przypadku większości metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejs reprezentuje podzestaw zaimplementowanego w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsie. Podzbiór zawiera obsługę interfejsu użytkownika IntelliSense, możliwość tworzenia karetki i wyboru oraz prostą funkcję wymiany tekstu. Ponadto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejs włącza oddzielne funkcje IntelliSense "podmiot" i "kontekst", dzięki czemu można zapewnić technologię IntelliSense dla podmiotów, które nie znajdują się bezpośrednio w buforze tekstu, który jest używany w kontekście.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>Dostawca interfejsu musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> metodę, aby umożliwić klientowi określenie typu funkcji IntelliSense obsługiwanych przez hosta.  
  
 Flagi hosta zdefiniowane w [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)są zestawione poniżej.  
  
|Flaga hosta IntelliSense|Opis|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Ustawienie tej flagi oznacza, że bufor kontekstu jest tylko do odczytu i edycja odbywa się tylko w tekście tematu.|  
|IHF_NOSEPERATESUBJECT|Ustawienie tej flagi oznacza, że nie ma osobnego tematu IntelliSense. Temat istnieje w buforze kontekstu, na przykład w tradycyjnym <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> systemie IntelliSense.|  
|IHF_SINGLELINESUBJECT|Ustawienie tej flagi oznacza, że podmiot nie obsługuje wielowierszowego, na przykład w jednym wierszu Edytuj w oknie **czujki** .|  
|IHF_FORCECOMMITTOCONTEXT|Jeśli ta flaga jest ustawiona i należy zaktualizować bufor kontekstu, Host włącza flagę tylko do odczytu w buforze kontekstu, która ma być ignorowana, a następnie edytuje w celu przejścia.|  
|IHF_OVERTYPE|Edytowanie (w temacie lub kontekście) powinno odbywać się w trybie zastępowania.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit i IVsIntellisenseHost. AfterCompletorCommit  
 Te metody wywołania zwrotnego są wywoływane przez okno uzupełniania przed i po zatwierdzeniu tekstu, aby umożliwić wstępne przetwarzanie i przetwarzanie końcowe.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>Interfejs to Współtworzenie wersji standardowego okna zakończenia, które jest używane przez zintegrowane środowisko programistyczne (IDE). Każdy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejs może szybko zaimplementować funkcję IntelliSense przy użyciu tego interfejsu completor.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
