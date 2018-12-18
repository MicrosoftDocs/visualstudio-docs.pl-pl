---
title: Lista zdarzeń graficznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 497ee3fe1c588c84195a544179d0d2955b1932b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766210"
---
# <a name="graphics-event-list"></a>Lista zdarzeń grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umożliwia Lista zdarzeń graficznych w analizatora grafiki programu Visual Studio Eksploruj zdarzenia Direct3D, które zostały zarejestrowane podczas renderowania ramki grach i aplikacjach.  
  
 Jest to lista zdarzeń:  
  
 ![Lista zdarzeń, które mają "Index" w nazwie. ](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Przy użyciu listy zdarzeń  
 Po wybraniu zdarzenia w przypadku listy, jego ma odzwierciedlone w informacje, które jest wyświetlane za pomocą innych narzędzi analizy grafiki; za pomocą listy zdarzeń w połączeniu z innych narzędzi można zbadać problem z renderowaniem szczegółowo w celu ustalenia jego przyczyny. Aby dowiedzieć się, jak rozwiązać problemy z renderowaniem, używając listy zdarzeń, razem z innymi narzędziami analizy grafiki, zobacz [przykłady](../debugger/graphics-diagnostics-examples.md).  
  
 Skutecznego korzystania z funkcji listy zdarzeń jest ważne dla poruszanie się po złożone klatek, które mogą zawierać tysięcy zdarzeń. Efektywne wykorzystanie listy zdarzeń wybierz widok działa najlepiej dla Ciebie, użyć wyszukiwania, aby filtrować listę zdarzeń, skorzystaj z linków, aby dowiedzieć się więcej o obiekty Direct3D, które są skojarzone ze zdarzeniem oraz za pomocą strzałki przycisków, aby przenosić między narysuj szybko wywołania.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Oznaczone kolorami zdarzenia w Direct3D 12  
 Direct3D 12 udostępnia wiele kolejek, które odnoszą się do funkcji z innego sprzętu. Aby ułatwić identyfikację kolejki, który jest skojarzony ze zdarzeniem grafiki określonego w Direct3D 12, zdarzenia są oznaczone kolorami zgodnie z ich kolejki na liście zdarzeń podczas pracy z przechwytywania aplikacji Direct3D 12.  
  
|Direct3D 12 kolejki|Kolor|  
|-----------------------|-----------|  
|Renderowanie kolejki|Zielony|  
|Obliczenia kolejki|Żółty|  
|Kolejka kopiowania|Pomarańczowy|  
  
 Direct3D 11 nie uwidocznić wielu kolejek, więc zdarzenia nie są oznaczone kolorami listy zdarzeń podczas pracy z przechwytywania aplikacji Direct3D 11.  
  
### <a name="event-list-views"></a>Widoki list zdarzeń  
 Lista zdarzeń obsługuje dwa różne widoki, pozwalające organizować zdarzenia grafiki na różne sposoby do obsługi przepływu pracy i preferencje. Jest to pierwszy widok *rysowania wywołuje widok* który organizuje zdarzenia i ich stan skojarzony hierarchicznie. Drugi widok jest *widok osi czasu* zdarzenia który organizuje chronologicznie, w formie płaskiej listy.  
  
 **Funkcję wywołania rysowania** widoku  
 Przechwycone zdarzenia i ich stan w hierarchii. Najwyższego poziomu hierarchii składają się zdarzenia, takie jak wywołania rysowania, czyści, obecny i te, w których za pomocą widoków. W przypadku listy, możesz wywołania rysowania można rozwijać w celu wyświetlenia stanu urządzenia, które były aktualne w momencie zgłoszenia wywołania rysowania; i możesz można rozwijać każdy stan, aby wyświetlić zdarzenia modyfikujące jego wartości. Na tym poziomie widać również, czy określony stan został ustawiony w poprzedniej ramki, jeśli została ustawiona więcej niż jeden raz od czasu ostatniego wywołania rysowania.  
  
 **Osi czasu** widoku  
 Wyświetla każde zdarzenie przechwycone w porządku chronologicznym. Ten sposób organizowania Lista zdarzeń jest taka sama, jak w poprzednich wersjach programu Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Aby zmienić tryb widoku listy zdarzeń  
  
-   W **Lista zdarzeń graficznych** Znajdź okno powyżej listy zdarzeń, **widoku** listy rozwijanej i wybierz **osi czasu** widoku lub **wywołaniarysowania** widoku.  
  
### <a name="filtering-events"></a>Filtrowanie zdarzeń  
 Można użyć pola wyszukiwania — znajdującego się w prawym górnym rogu **Lista zdarzeń graficznych** okna — Aby filtrować listę zdarzeń, aby uwzględnić tylko zdarzenia, których nazwy zawierają konkretnych słów kluczowych. Można określić pojedynczy słów kluczowych, takich jak `Vertex`— jak pokazano na poprzedniej ilustracji — lub wiele słów kluczowych, korzystając z rozdzielaną średnikami listę `Draw;Primitive`— który dopasowuje zdarzenia, które mają jedną `Draw` lub `Primitive` w nazwach. Wyszukiwania są wrażliwe na białe znaki — na przykład `VSSet` i `VS Set` są różne wyszukiwania — więc upewnij się, że formularz wyszukiwania ostrożnie.  
  
### <a name="moving-between-draw-calls"></a>Przenoszenie między wywołaniami rysowania  
 Ponieważ badanie `Draw` wywołań jest szczególnie ważne, można użyć **przejdź do następnego wywołania rysowania** i **przejdź do poprzedniego wywołania rysowania** przyciski — znajdującego się w lewym górnym rogu **Lista zdarzeń graficznych** okna, aby znaleźć i szybkie przenoszenie między wywołaniami rysowania.  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby poznać niektóre zdarzenia grafiki, może być konieczne dodatkowe informacje dotyczące bieżącego stanu Direct3D lub obiekty Direct3D, które są przywoływane przez zdarzenie. Wiele zdarzeń zawierają łącza do tych informacji, które można wykonać, aby uzyskać więcej szczegółów.  
  
## <a name="kinds-of-events-and-event-markers"></a>Rodzaje zdarzeń i znaczników zdarzeń  
 Zdarzenia, które są wyświetlane w przypadku listy są zorganizowane w cztery kategorie: Ogólne zdarzenia rysowania zdarzenia, grup zdarzeń zdefiniowanych przez użytkownika i znaczniki zdarzenie zdefiniowane przez użytkownika. Z wyjątkiem zdarzenia ogólne każde zdarzenie jest wyświetlana wraz z ikonami oznaczającymi, należącego do kategorii.  
  
|Ikona|Opis zdarzenia|  
|----------|-----------------------|  
|(Brak ikony)|Zdarzenia ogólne<br /> Dowolne zdarzenie, który nie jest zdarzenie zdefiniowane przez użytkownika, grupy zdarzeń zdefiniowanych przez użytkownika lub sięganie zdarzeń.|  
|![Ikona Zdarzenie draw](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Zdarzenia rysowania<br /> Oznacza zdarzenia remis, które wystąpiły podczas przechwyconej ramki.|  
|![Użytkownik&#45;zdefiniowane ikony znacznika zdarzenia](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Grupa zdarzeń zdefiniowanych przez użytkownika<br /> Grupy zdarzenia związane z, zgodnie z definicją w aplikacji.|  
|![Użytkownik&#45;zdefiniowane ikony znacznika zdarzenia](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Znacznik zdarzenia zdefiniowane przez użytkownika<br /> Oznacza określonej lokalizacji, zgodnie z definicją w aplikacji.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Oznaczanie zdarzeń zdefiniowanych przez użytkownika w aplikacji  
 Zdarzenia zdefiniowane przez użytkownika są specyficzne dla aplikacji. Ich umożliwia korelowanie istotne zdarzenia, które wystąpiły w aplikacji za pomocą zdarzeń na liście zdarzeń grafiki. Na przykład można utworzyć grupy zdarzeń zdefiniowanych przez użytkownika w celu uporządkowania zdarzeń powiązanych — takich jak te, które renderują interfejsu użytkownika — na grupy i hierarchie są tak, aby łatwiej przeglądać listę zdarzeń, lub możesz utworzyć znaczniki, gdy niektóre rodzaje obiektów rysowany tak, aby można łatwo znaleźć listy zdarzeń ich zdarzenia grafiki.  
  
 Aby utworzyć grupy i znaczników w swojej aplikacji, należy użyć tych samych interfejsów API, który program Direct3D oferuje do użytku przez inne Direct3D, narzędzia debugowania. Te interfejsy API czasami się zmieniać między wersjami programu Direct3D, ale podstawowa funkcjonalność jest taka sama.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Zdarzeń zdefiniowanych przez użytkownika w Direct3D 12  
 Aby utworzyć grupy i znaczników w Direct3D 12, przy użyciu interfejsów API, opisane w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, które można użyć w zależności od tego, czy są oznaczanie zdarzeń w kolejce poleceń, czy polecenie listy.  
  
|Opis interfejsu API|[ID3D12CommandQueue](https://msdn.microsoft.com/library/dn788627.aspx)|[ID3D12GraphicsCommandList](https://msdn.microsoft.com/library/dn903537.aspx)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Sprawdź dostępność zdarzenie zdefiniowane przez użytkownika|[PIXGetStatus](http://msdn.microsoft.com/en-us/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](http://msdn.microsoft.com/en-us/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Rozpocznij grupy zdarzeń|[PIXBeginEvent](http://msdn.microsoft.com/en-us/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](http://msdn.microsoft.com/en-us/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|W końcu grupy zdarzeń|[PIXEndEvent](http://msdn.microsoft.com/en-us/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](http://msdn.microsoft.com/en-us/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Utwórz — znacznik zdarzenia|[PIXSetMarker](http://msdn.microsoft.com/en-us/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](http://msdn.microsoft.com/en-us/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Zdarzenia zdefiniowane przez użytkownika w programie Direct3D 11 i jego starszych wersji  
 Aby utworzyć grupy i znaczniki w interfejsie Direct3D 11 lub wcześniej, przy użyciu interfejsów API, opisane w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, które służy do różnych wersji programu Direct3D 11 i starszych wersji Direct3D.  
  
|Opis interfejsu API|[ID3D11DeviceContext2](http://msdn.microsoft.com/library/windows/desktop/dn280498.aspx) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|Rodzina D3DPerf_ interfejsu API (Direct3D 11.0 i starsze)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Rozpocznij grupy zdarzeń|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|W końcu grupy zdarzeń|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Utwórz — znacznik zdarzenia|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Można użyć dowolnego z tych interfejsów API, które obsługuje daną wersję programu Direct3D — na przykład, jeśli są przeznaczone dla interfejsu API Direct3D 11.1, możesz użyć albo `SetMarker` lub `D3DPerf_SetMarker` utworzyć znacznika zdarzenia, ale nie `SetMarkerInt` ponieważ jej dostępność tylko w Direct3D 11.2 — a nawet można łączyć te, które obsługują różne wersje programu Direct3D ze sobą w tej samej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów spowodowany stanem urządzenia](../debugger/walkthrough-missing-objects-due-to-device-state.md)



