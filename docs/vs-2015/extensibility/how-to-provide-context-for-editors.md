---
title: 'Instrukcje: udostępnianie kontekstu dla edytorów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858304"
---
# <a name="how-to-provide-context-for-editors"></a>Instrukcje: dostarczanie kontekstu edytorom
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku edytora kontekst jest aktywny tylko wtedy, gdy Edytor ma fokus lub miał fokus bezpośrednio przed przeniesieniem fokusu do okna narzędzi. Kontekst dla edytora można podać, wykonując następujące czynności:  
  
1. Utwórz zbiór kontekstowy.  
  
2. Opublikuj zbiór kontekstowy do wyboru identyfikatora elementu (SEID).  
  
3. Zachowaj kontekst w zbiorze.  
  
   Te zadania są objęte następującymi procedurami. Aby uzyskać więcej informacji na temat udostępniania kontekstu, zobacz temat **niezawodne programowanie** w dalszej części tego tematu.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Aby utworzyć zbiór kontekstowy dla edytora lub projektanta  
  
1. Wywołaj `QueryService` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> usługi.  
  
     Zwracany jest wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfejsu.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodę, aby utworzyć nowy kontekst lub zbiór kontekstowy.  
  
     Zwracany jest wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfejsu.  
  
3. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> metodę, aby dodać atrybuty, słowa kluczowe Lookup lub F1 słowa kluczowe do kontekstu lub podzbioru kontekstu.  
  
4. Jeśli tworzysz zbiór kontekstowy, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodę w celu połączenia z zbiorem kontekstu podrzędnego z zbiorem kontekstu nadrzędnego.  
  
5. Wywołaj, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> Aby otrzymać powiadomienie, gdy **dynamiczne okno pomocy** ma zostać zaktualizowane.  
  
     Gdy **dynamiczne okno pomocy** wywołuje Edytor, gdy jest gotowy do aktualizacji, umożliwia opóźnienie zmiany kontekstu do momentu aktualizacji. W ten sposób można zwiększyć wydajność, ponieważ pozwala to opóźnić wykonywanie czasochłonnych algorytmów do momentu udostępnienia czasu bezczynności systemu.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Aby opublikować zbiór kontekstowy do SEID  
  
1. Wywołaj `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> usługę, aby zwrócić wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfejsu.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , określając wartość identyfikatora elementu ( `elementid` parametr) SEID_UserContext, aby wskazać, że jest przekazywany kontekst do poziomu globalnego.  
  
3. Gdy Edytor lub Projektant staną się aktywne, wartości w jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> obiekcie są propagowane do zaznaczenia globalnego. Wystarczy wykonać ten proces tylko raz dla każdej sesji, a następnie przechowywać wskaźnik do globalnego kontekstu utworzonego po wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Aby zachować zbiór kontekstu  
  
1. Zaimplementuj, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> Aby upewnić się, że **dynamiczne okno pomocy** wywołuje Edytor lub projektanta przed aktualizacją.  
  
     Dla każdego zbioru kontekstu, który został wywołany <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> po utworzeniu zbioru kontekstu i jego implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> do powiadomienia dostawcy kontekstu, że zostanie zaktualizowany zbiór kontekstowy. Można użyć tego wywołania, aby zmienić atrybuty i słowa kluczowe w zbiorze kontekstowym oraz w każdym wypełnieniu kontekstu, przed aktualizacją **dynamicznego okna pomocy** .  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> w zbiorze kontekstu, aby wskazać, że edytor lub Projektant ma nowy kontekst.  
  
     Gdy **dynamiczne okno pomocy** wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , aby wskazać, że jest aktualizowane, Edytor lub Projektant może zaktualizować kontekst odpowiednio dla zbioru kontekstu nadrzędnego i wszystkich odniesień kontekstu w tym czasie.  
  
    > [!NOTE]
    > `SetDirty`Flaga jest automatycznie ustawiana na `true` zawsze, gdy kontekst jest dodawany lub usuwany z zbioru kontekstowego. **Dynamiczne okno pomocy** wywołuje tylko <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> w zbiorze kontekstu, jeśli `SetDirty` flaga jest ustawiona na `true` . Jest resetowany do `false` po aktualizacji.  
  
3. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> dodania kontekstu do aktywnej kolekcji kontekstu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> usunięcia kontekstu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W przypadku pisania własnych edytorów należy wykonać wszystkie trzy procedury przedstawione w tym temacie, aby zapewnić kontekst edytora.  
  
> [!NOTE]
> Aby prawidłowo aktywować Edytor lub okno projektanta i upewnić się, że routing poleceń jest prawidłowo aktualizowany, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> składnik, aby uczynić go oknem koncentracji uwagi.  
  
 SEID to zbiór właściwości, które zmieniają się w zależności od wyboru. Informacje SEID są dostępne za pomocą wyboru globalnego. Globalne zaznaczenie jest przewodne do zdarzeń wyzwalanych przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfejs i zawiera listę wszystkich wybranych elementów (bieżący edytor, bieżące okno narzędzi, Bieżąca hierarchia itd.).  
  
 W przypadku edytorów i projektantów, w których kontekst można zmienić za każdym razem, gdy kursor znajduje się w obrębie wyrazu, jest nieefektywna, aby stale aktualizować zbiór kontekstowy. Aby aktualizowanie było skuteczniejsze w dowolnym momencie, gdy wykryjesz kursor w edytorze lub oknie projektanta, możesz wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Dzięki temu można przechowywać zmiany kontekstu do czasu bezczynności, a usługa kontekstu IDE wysyła powiadomienie do edytora lub projektanta, że **dynamiczne okno pomocy** jest aktualizowane. Ta metoda jest używana w procedurze "aby zachować zbiór kontekstów" w tym temacie.  
  
 Po dostarczeniu kontekstu dla działań w ramach edytora lub projektanta należy podać określone słowo kluczowe F1, aby umożliwić użytkownikom uzyskanie pomocy dotyczącej edytora lub projektanta.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
