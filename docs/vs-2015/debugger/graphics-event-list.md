---
title: Lista zdarzeń grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b1d8bdeb4497af57c385e73ff0dcd34041a2097
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297328"
---
# <a name="graphics-event-list"></a>Lista zdarzeń grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj listy zdarzeń grafiki w analizator grafiki programu Visual Studio, aby eksplorować zdarzenia Direct3D, które zostały zarejestrowane podczas renderowania ramki gry lub aplikacji.  
  
 Jest to lista zdarzeń:  
  
 ![Lista zdarzeń o nazwie "index".](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Korzystanie z listy zdarzeń  
 Po wybraniu zdarzenia na liście zdarzeń zostanie ono odzwierciedlone w informacjach wyświetlanych przez inne narzędzia do analizy grafiki; Korzystając z listy zdarzeń w połączeniu z tymi innymi narzędziami, można szczegółowo sprawdzić problem z renderowaniem w celu ustalenia jego przyczyny. Aby dowiedzieć się więcej o sposobach rozwiązywania problemów z renderowaniem przy użyciu listy zdarzeń wraz z innymi narzędziami do analizy grafiki, zobacz [przykłady](../debugger/graphics-diagnostics-examples.md).  
  
 Efektywne korzystanie z funkcji listy zdarzeń jest ważne dla zaawansowania ramek, które mogą zawierać tysiące zdarzeń. Aby efektywnie korzystać z listy zdarzeń, wybierz widok najlepiej sprawdza się dla Ciebie, użyj wyszukiwania do filtrowania listy zdarzeń, postępuj zgodnie z linkami, aby dowiedzieć się więcej na temat obiektów Direct3D, które są skojarzone ze zdarzeniem, i użyj przycisków strzałek, aby szybko przełączać się między wywołaniami rysowania.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Zdarzenia kodowane kolorem w programie Direct3D 12  
 Direct3D 12 uwidacznia wiele kolejek, które odpowiadają różnym funkcjom sprzętowym. Aby ułatwić zidentyfikowanie kolejki skojarzonej z konkretnym zdarzeniem grafiki w programie Direct3D 12, zdarzenia są kodowane kolorami na liście zdarzeń zgodnie z ich kolejką podczas pracy z funkcją przechwytywania aplikacji Direct3D 12.  
  
|Kolejka Direct3D|Kolor|  
|-----------------------|-----------|  
|Kolejka renderowania|Znacznika|  
|Kolejka obliczeń|Kryje|  
|Kopiuj kolejkę|Pomarańcz|  
  
 Program Direct3D 11 nie uwidacznia wielu kolejek, dlatego zdarzenia nie są kodowane na liście zdarzeń podczas pracy z funkcją przechwytywania aplikacji Direct3D 11.  
  
### <a name="event-list-views"></a>Widoki listy zdarzeń  
 Lista zdarzeń obsługuje dwa różne widoki, które organizują zdarzenia grafiki na różne sposoby obsługi przepływu pracy i preferencji. Pierwszy widok to *Widok wywołania rysowania* , który organizuje zdarzenia i ich stan skojarzony hierarchicznie. Drugi widok to *Widok osi czasu* , który organizuje zdarzenia chronologicznie, na płaskiej liście.  
  
 Widok **połączeń rysowania**  
 Wyświetla przechwycone zdarzenia i ich stan w hierarchii. Najwyższego poziomu hierarchii składają się z zdarzeń, takich jak wywołania rysowania, czyszczenia, obecności i tych, które są związane z widokami. Na liście zdarzeń można rozwinąć wywołania rysowania, aby wyświetlić stan urządzenia, który był aktualny w momencie wywołania remisu; można również rozszerzyć każdy rodzaj stanu, aby wyświetlić zdarzenia ustawiające ich wartości. Na tym poziomie można także sprawdzić, czy określony stan został ustawiony w poprzedniej klatce lub czy został ustawiony więcej niż jeden raz od ostatniego wywołania rysowania.  
  
 Widok **osi czasu**  
 Wyświetla każde przechwycone zdarzenie w kolejności chronologicznej. Ten sposób organizowania listy zdarzeń jest taki sam jak w poprzednich wersjach programu Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Aby zmienić tryb widoku listy zdarzeń  
  
- W oknie **Lista zdarzeń grafiki** , powyżej listy zdarzeń, zlokalizuj listę rozwijaną **Widok** i wybierz widok **oś czasu** lub widok **wywołania rysowania** .  
  
### <a name="filtering-events"></a>Filtrowanie zdarzeń  
 Możesz użyć pola wyszukiwania — znajdującego się w prawym górnym rogu okna **Lista zdarzeń grafiki** — aby przefiltrować listę zdarzeń w celu uwzględnienia tylko zdarzeń, których nazwy zawierają określone słowa kluczowe. Możesz określić pojedyncze słowa kluczowe, takie jak `Vertex`— jak pokazano na poprzedniej ilustracji — lub kilka słów kluczowych przy użyciu listy rozdzielanej średnikami, takiej jak `Draw;Primitive`— które pasują do zdarzeń, które mają `Draw` lub `Primitive` nazwy. Wyszukiwania są wrażliwe na odstępy — na przykład `VSSet` i `VS Set` są różnymi wyszukiwaniami, dlatego należy uważnie przeszukiwać dane.  
  
### <a name="moving-between-draw-calls"></a>Przechodzenie między wywołaniami rysowania  
 Ponieważ badanie wywołań `Draw` jest szczególnie ważne, można użyć **przejść do następnego wywołania rysowania** i **przejść do poprzedniego przycisku rysowania wywołania** — znajdującego się w lewym górnym rogu okna **Lista zdarzeń grafiki** — w celu szybkiego znalezienia i przechodzenia między wywołaniami rysowania.  
  
### <a name="links-to-graphics-objects"></a>Linki do obiektów graficznych  
 W celu zrozumienia pewnych zdarzeń graficznych mogą być potrzebne dodatkowe informacje o bieżącym stanie Direct3D lub obiektów Direct3D, do których odwołuje się zdarzenie. Wiele zdarzeń zawiera linki do tych informacji, które można wykonać, aby uzyskać więcej szczegółów.  
  
## <a name="kinds-of-events-and-event-markers"></a>Rodzaje zdarzeń i znaczniki zdarzeń  
 Zdarzenia, które są wyświetlane na liście zdarzeń, są zorganizowane w cztery kategorie: zdarzenia ogólne, narysuj zdarzenia, zdefiniowane przez użytkownika grupy zdarzeń i znaczniki zdarzeń zdefiniowane przez użytkownika. Z wyjątkiem ogólnych zdarzeń każde zdarzenie jest wyświetlane wraz z ikoną wskazującą kategorię, do której należy.  
  
|Ikona|Opis zdarzenia|  
|----------|-----------------------|  
|(brak ikony)|Zdarzenie ogólne<br /> Każde zdarzenie, które nie jest zdarzeniem zdefiniowanym przez użytkownika, grupą zdarzeń zdefiniowanym przez użytkownika lub zdarzeniem remisu.|  
|![Ikona zdarzenia rysowania](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Rysuj wydarzenie<br /> Oznacza zdarzenie rysowania, które wystąpiło w przechwyconej ramce.|  
|![Ikona znacznika&#45;zdarzenia zdefiniowanego przez użytkownika](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Grupa zdarzeń zdefiniowana przez użytkownika<br /> Grupuje zdarzenia pokrewne zdefiniowane przez aplikację.|  
|![Ikona znacznika&#45;zdarzenia zdefiniowanego przez użytkownika](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Znacznik zdarzenia zdefiniowany przez użytkownika<br /> Oznacza określoną lokalizację zdefiniowaną przez aplikację.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Oznaczanie zdarzeń zdefiniowanych przez użytkownika w aplikacji  
 Zdarzenia zdefiniowane przez użytkownika są specyficzne dla Twojej aplikacji. Można ich użyć do skorelowania poważnych zdarzeń występujących w aplikacji ze zdarzeniami na liście zdarzeń grafiki. Można na przykład utworzyć grupy zdarzeń zdefiniowane przez użytkownika, aby organizować powiązane zdarzenia, takie jak te, które renderują interfejs użytkownika w grupach lub hierarchiach, dzięki czemu można łatwiej przeglądać listę zdarzeń. można też tworzyć znaczniki, gdy niektóre obiekty są narysowana, aby można było łatwo znaleźć na liście zdarzeń swoje zdarzenia graficzne.  
  
 Aby utworzyć grupy i znaczniki w aplikacji, należy użyć tych samych interfejsów API, które są dostępne dla innych narzędzi debugowania Direct3D przez program Direct3D. Te interfejsy API czasami zmieniają się między wersjami programu Direct3D, ale podstawowe funkcje są takie same.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Zdarzenia zdefiniowane przez użytkownika w programie Direct3D 12  
 Aby utworzyć grupy i znaczniki w programie Direct3D 12, Użyj interfejsów API opisanych w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, których można użyć w zależności od tego, czy oznaczasz zdarzenia w kolejce poleceń, czy na liście poleceń.  
  
|Opis interfejsu API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Sprawdź dostępność zdarzeń zdefiniowanych przez użytkownika|[PIXGetStatus](https://msdn.microsoft.com/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](https://msdn.microsoft.com/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Rozpocznij pracę grupy zdarzeń|[PIXBeginEvent](https://msdn.microsoft.com/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](https://msdn.microsoft.com/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Zakończ grupę zdarzeń|[PIXEndEvent](https://msdn.microsoft.com/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](https://msdn.microsoft.com/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Tworzenie znacznika zdarzenia|[PIXSetMarker](https://msdn.microsoft.com/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](https://msdn.microsoft.com/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Zdarzenia zdefiniowane przez użytkownika w programie Direct3D 11 i starszych wersjach  
 Aby utworzyć grupy i znaczniki w programie Direct3D 11 lub starszym, Użyj interfejsów API opisanych w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, których można użyć dla różnych wersji programu Direct3D 11 i starszych wersji programu Direct3D.  
  
|Opis interfejsu API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11,2)|[ID3DUserDefinedAnnotation](https://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11,1)|Rodzina interfejsów API D3DPerf_ (Direct3D 11,0 i starsze)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Rozpocznij pracę grupy zdarzeń|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Zakończ grupę zdarzeń|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Tworzenie znacznika zdarzenia|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Możesz użyć dowolnego z tych interfejsów API, które obsługuje wersja Direct3D — na przykład, jeśli docelowym interfejsem API programu Direct3D 11,1, możesz użyć albo `SetMarker` lub `D3DPerf_SetMarker` do utworzenia znacznika zdarzenia, ale nie `SetMarkerInt`, ponieważ jest on dostępny tylko w programie Direct3D 11.2 — i można nawet mieszać te, które obsługują różne wersje programu Direct3D razem w tej samej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów spowodowany stanem urządzenia](../debugger/walkthrough-missing-objects-due-to-device-state.md)
