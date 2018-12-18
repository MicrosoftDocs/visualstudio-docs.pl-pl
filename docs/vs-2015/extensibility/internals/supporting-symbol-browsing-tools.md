---
title: Obsługa narzędzi do przeglądania symboli | Dokumentacja firmy Microsoft
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
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c4cf9f711990f5b3f1f064aa6311a8b33b64fef
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757690"
---
# <a name="supporting-symbol-browsing-tools"></a>Obsługa narzędzi do przeglądania symboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Przeglądarka obiektów**, **Widok klas**, **przeglądarce wywołań** i **wyniki wyszukiwania symboli** narzędzia udostępniają symbol przeglądania w programie Visual Studio. Te narzędzia wyświetlanie widoków drzewa hierarchicznego symboli i pokazanie relacji między symbolami w drzewie. Symbole mogą reprezentować przestrzenie nazw, obiektów, klas, składowych klasy i inne elementy języka zawarte w różnych składników. Składniki obejmują projektów programu Visual Studio, zewnętrzne [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] składniki i biblioteki typów (.tlb). Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Biblioteki przeglądania symboli  
 Jako implementującego języka możesz rozszerzyć możliwości przeglądania symboli programu Visual Studio, tworząc bibliotek, Śledź symbole w poszczególnych składnikach, które zapewniają listy symboli do Menedżera obiektów programu Visual Studio za pomocą zestawu interfejsów. Biblioteka jest opisana przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfejsu. Menedżer obiektów programu Visual Studio odpowiada na żądania dla nowych danych narzędzi do przeglądania symboli przez uzyskanie danych z biblioteki i organizowania go. Następnie wypełnia lub narzędzia zostaje zaktualizowana o żądanych danych. Aby uzyskać odwołanie do Menedżera obiektów w programie Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, przekazać <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identyfikator do usługi `GetService` metody.  
  
 Każdej biblioteki należy zarejestrować przy użyciu Menedżera obiektów programu Visual Studio, który gromadzi informacje o wszystkich bibliotek. Aby zarejestrować bibliotekę, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. W zależności od narzędzie, które inicjuje żądanie Menedżer obiektów programu Visual Studio znajdzie odpowiednią bibliotekę i żąda danych. Dane przesyłane między bibliotekami i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżera obiektów na listach symbole opisanego przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfejsu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżera obiektów jest odpowiedzialny za okresowego odświeżania narzędzi do przeglądania symboli do odzwierciedlenia najnowszych danych zawartych w bibliotekach.  
  
 Poniższy diagram zawiera przykład kluczowe elementy procesu wymiany żądań/danych między biblioteką a Menedżera obiektów programu Visual Studio. Interfejsy na diagramie są częścią aplikacji kodu zarządzanego.  
  
 ![Przepływ danych między biblioteką a Menedżera obiektów](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Aby utworzyć listy symboli dla Menedżera obiektów programu Visual Studio, musisz najpierw zarejestrować biblioteki z Menedżera obiektów programu Visual Studio przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. Po zarejestrowaniu biblioteki menedżera obiektów programu Visual Studio żądań pewne informacje na temat funkcji biblioteki. Na przykład żądania flagi biblioteki i obsługiwane kategorie, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metody. W pewnym momencie, gdy jedno z narzędzi żąda danych z tej biblioteki menedżera obiektów żądań najwyższego poziomu lista symboli przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metody. W odpowiedzi biblioteki są produkowane lista symboli i udostępniła je systemowi Menedżera obiektów programu Visual Studio za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfejsu. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżera obiektów określa, ile elementów znajdują się na liście, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metody. Wszystkie następujące żądania odnoszą się do danego elementu na liście i podaj numer indeksu elementu w każdym żądaniu. Menedżer obiektów programu Visual Studio przechodzi zbierać informacje dotyczące typu, dostępności i inne właściwości elementu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metody.  
  
 Określa nazwę elementu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metody i żądania informacje o ikonie przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metody. Ikona jest wyświetlana na lewo od nazwy elementu i przedstawia typ elementu, dostępności i inne właściwości.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Obiekt Menedżera wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodę, aby ustalić, czy element danej listy można rozwijać i zawiera elementy podrzędne. Jeśli interfejs użytkownika wysyła żądanie, aby rozwinąć element, Menedżera obiektów żądania podrzędnego lista symboli, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metody. Proces jest kontynuowany, za pomocą różnych częściach drzewa kompilowana na żądanie.  
  
> [!NOTE]
>  Aby zaimplementować dostawcę symbolu kodu natywnego, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfejsów.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: rejestrowanie biblioteki przy użyciu Menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Instrukcje: Uwidacznianie listy symboli udostępnianych przez bibliotekę dla Menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Instrukcje: identyfikowanie symboli w bibliotece](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)

