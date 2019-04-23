---
title: 'Instrukcje: Dostarczanie kontekstu edytory | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: e5900d5c818883ffc78b2399b937c80307b52c36
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116527"
---
# <a name="how-to-provide-context-for-editors"></a>Instrukcje: Dostarczanie kontekstu edytorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W edytorze kontekst jest aktywne, tylko wtedy, gdy Edytor ma fokus lub były wcześniej fokus natychmiast fokus został przeniesiony do okna narzędzi. Możesz podać kontekstu edytora, wykonując następujące czynności:  
  
1. Utwórz pakiet z kontekstu.  
  
2. Opublikuj pakiet kontekstu identyfikatora elementu wyboru (SEID).  
  
3. Obsługa kontekstu w zbiorze.  
  
   Te zadania są objęte następujące procedury. Aby uzyskać więcej informacji na temat kontekstem wskazującym, zobacz **niezawodne programowania** w dalszej części tego tematu.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Aby utworzyć pakiet z kontekstu dla edytora lub projektanta  
  
1. Wywołaj `QueryService` na Twoje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs na potrzeby <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> usługi.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> zwracany jest interfejs.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodę, aby utworzyć nowy zbiór kontekstu lub kontekst podrzędny.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> zwracany jest interfejs.  
  
3. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> metodę, aby dodać atrybuty, wyszukiwanie słów kluczowych lub słów kluczowych F1 do zbioru kontekstu lub kontekst podrzędny.  
  
4. Jeśli tworzysz pakiet kontekst podrzędny wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodę, aby połączyć zbiór kontekst podrzędny zbiór kontekst nadrzędnego.  
  
5. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> aby otrzymać powiadomienie po **dynamiczna Pomoc** okno jest aktualizacja.  
  
     Posiadanie **dynamiczna Pomoc** okno wywołanie edytora podczas jest gotowy do aktualizacji daje możliwość opóźnienia, zmieniając kontekstu, dopóki nie wystąpi aktualizacji. W ten sposób można poprawić wydajność, ponieważ umożliwia opóźnienie uruchamiania algorytmy czasochłonne, aż do czasu bezczynności systemu.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Aby opublikować pakiet kontekstu SEID  
  
1. Wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> usługę, aby zwrócić wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfejsu.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, określając identyfikator elementu (`elementid` parametr) wartość SEID_UserContext, aby wskazać, że przekazujesz kontekstu na poziomie globalnym.  
  
3. Gdy edytora lub projektanta stanie się aktywny, wartości w jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> obiektu są propagowane do globalnego zaznaczenia. Konieczne jest ukończenie tego procesu na początku sesji, a następnie umieść wskaźnik do kontekście globalnym utworzone podczas wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Aby zachować zbiór kontekstu  
  
1. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> do upewnij się, że **dynamiczna Pomoc** wywołuje okna edytora lub projektanta przed jego aktualizacji.  
  
     Dla każdego zbioru kontekstu, który jest nazywany <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> po zbiorze kontekstu jest tworzony i została zaimplementowana <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> powiadomić dostwcy kontekstu zostanie zaktualizowany pakiet kontekstu. To wywołanie służy do zmiany atrybutów i słowa kluczowe w zbiorze kontekstu i w dowolnym zbiory kontekst podrzędny przed **dynamiczna Pomoc** występuje Windows update.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> na zbiór kontekstu, aby wskazać, że edytora lub projektanta ma nowy kontekst.  
  
     Gdy **dynamiczna Pomoc** wywołania okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> aby wskazać, że jest on aktualizowany, edytora lub projektanta, można zaktualizować kontekstu odpowiednio do zbioru kontekst nadrzędnego i wszystkie zbiory kontekst podrzędny w tej chwili.  
  
    > [!NOTE]
    >  `SetDirty` Flaga jest automatycznie ustawiana na `true` zawsze, gdy kontekst jest dodane lub usunięte z pakietu kontekstu. **Dynamiczna Pomoc** okna tylko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> na zbiór kontekstu Jeśli `SetDirty` flaga jest ustawiona na `true`. Jest resetowana do `false` po aktualizacji.  
  
3. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> dodać kontekstowego do kolekcji aktywnego kontekstu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> usunąć kontekst.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli piszesz własnego edytora, należy wykonać wszystkie trzy procedury przedstawione w tym temacie, aby zapewnić kontekst dla edytora.  
  
> [!NOTE]
>  Aby prawidłowo Uaktywnij okno edytora lub projektanta i upewnij się, że routing poleceń są zaktualizowane prawidłowo, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> w składniku dokonanie okien fokus.  
  
 SEID to zbiór właściwości, które zmieniają się na podstawie wyboru. SEID informacje są dostępne za pośrednictwem globalnej zaznaczenia. Wybór globalnego jest podłączona do zdarzenia wyzwolone przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfejsu, i zawiera listę wszystkich elementów, która jest zaznaczone (bieżącego edytora, bieżącego okna narzędzi, bieżącej hierarchii i tak dalej).  
  
 Projektanci i edytory w kontekście, które można zmieniać zawsze, gdy kursor jest przenoszony w programie word jest nieefektywne stale zaktualizować pakiet kontekstu. Aby ułatwić aktualizowanie bardziej wydajne, ilekroć wykryć cursor poruszanie się edytora lub okna projektanta, można wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. W ten sposób pozwala na potrzeby przechowywania zmiany kontekstu czasu bezczynności i środowiska IDE kontekstu usługa wysyła powiadomienie do edytora lub projektanta, **dynamiczna Pomoc** okna jest aktualizowany. To podejście jest używany w procedurze "Aby obsługa zbiór kontekstu" w tym temacie.  
  
 Po podaniu kontekstu działań w ramach Twojego edytora lub projektanta, należy podać z określonym słowem kluczowym F1, aby użytkownicy mogli uzyskać pomoc dotyczącą edytora lub projektanta, sam.  
  
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
