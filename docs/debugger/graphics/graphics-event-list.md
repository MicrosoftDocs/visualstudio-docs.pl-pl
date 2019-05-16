---
title: Lista zdarzeń graficznych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a78fc8b1351f7a614421aabb344820ddc22ece24
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679444"
---
# <a name="graphics-event-list"></a>Lista zdarzeń grafiki
Umożliwia Lista zdarzeń graficznych w analizatora grafiki programu Visual Studio Eksploruj zdarzenia Direct3D, które zostały zarejestrowane podczas renderowania ramki grach i aplikacjach.

 Jest to lista zdarzeń:

 ![Lista zdarzeń, które mają "Index" w nazwie. ](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Przy użyciu listy zdarzeń
 Po wybraniu zdarzenia w przypadku listy, jego ma odzwierciedlone w informacje, które jest wyświetlane za pomocą innych narzędzi analizy grafiki; za pomocą listy zdarzeń w połączeniu z innych narzędzi można zbadać problem z renderowaniem szczegółowo w celu ustalenia jego przyczyny. Aby dowiedzieć się, jak rozwiązać problemy z renderowaniem, używając listy zdarzeń, razem z innymi narzędziami analizy grafiki, zobacz [przykłady](graphics-diagnostics-examples.md).

 Skutecznego korzystania z funkcji listy zdarzeń jest ważne dla poruszanie się po złożone klatek, które mogą zawierać tysięcy zdarzeń. Efektywne wykorzystanie listy zdarzeń wybierz widok działa najlepiej dla Ciebie, użyć wyszukiwania, aby filtrować listę zdarzeń, skorzystaj z linków, aby dowiedzieć się więcej o obiekty Direct3D, które są skojarzone ze zdarzeniem oraz za pomocą strzałki przycisków, aby przenosić między narysuj szybko wywołania.

### <a name="color-coded-events-in-direct3d-12"></a>Oznaczone kolorami zdarzenia w Direct3D 12
 Direct3D 12 udostępnia wiele kolejek, które odnoszą się do funkcji z innego sprzętu. Aby ułatwić identyfikację kolejki, który jest skojarzony ze zdarzeniem grafiki określonego w Direct3D 12, zdarzenia są oznaczone kolorami zgodnie z ich kolejki na liście zdarzeń podczas pracy z przechwytywania aplikacji Direct3D 12.

|Direct3D 12 Queue|Kolor|
|-----------------------|-----------|
|Renderowanie kolejki|Zielony|
|Obliczenia kolejki|Żółty|
|Kolejka kopiowania|Pomarańczowy|

 Direct3D 11 nie uwidocznić wielu kolejek, więc zdarzenia nie są oznaczone kolorami listy zdarzeń podczas pracy z przechwytywania aplikacji Direct3D 11.

### <a name="event-list-views"></a>Widoki list zdarzeń
 Lista zdarzeń obsługuje dwa różne widoki, pozwalające organizować zdarzenia grafiki na różne sposoby do obsługi przepływu pracy i preferencje. Jest to pierwszy widok *widok pracy procesora GPU* który organizuje zdarzenia i ich stan skojarzony hierarchicznie. Drugi widok jest *widok osi czasu* zdarzenia który organizuje chronologicznie, w formie płaskiej listy.

 **Działanie procesora GPU** widoku przechwycone zdarzenia i ich stan w hierarchii. Najwyższego poziomu hierarchii składają się zdarzenia, takie jak wywołania rysowania, czyści, obecny i te, w których za pomocą widoków. W przypadku listy, możesz wywołania rysowania można rozwijać w celu wyświetlenia stanu urządzenia, które były aktualne w momencie zgłoszenia wywołania rysowania; i możesz można rozwijać każdy stan, aby wyświetlić zdarzenia modyfikujące jego wartości. Na tym poziomie widać również, czy określony stan został ustawiony w poprzedniej ramki, jeśli została ustawiona więcej niż jeden raz od czasu ostatniego wywołania rysowania.

 **Osi czasu** każdego przechwycone zdarzenia w widoku są wyświetlane w porządku chronologicznym. Ten sposób organizowania Lista zdarzeń jest taka sama, jak w poprzednich wersjach programu Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Aby zmienić tryb widoku listy zdarzeń

- W **Lista zdarzeń graficznych** Znajdź okno powyżej listy zdarzeń, **widoku** listy rozwijanej i wybierz **osi czasu** widoku lub **działanie procesora GPU** widoku.

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
|![Ikona Zdarzenie draw](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Zdarzenia rysowania<br /> Oznacza zdarzenia remis, które wystąpiły podczas przechwyconej ramki.|
|![Użytkownik&#45;zdefiniowane ikony znacznika zdarzenia](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Grupa zdarzeń zdefiniowanych przez użytkownika<br /> Grupy zdarzenia związane z, zgodnie z definicją w aplikacji.|
|![Użytkownik&#45;zdefiniowane ikony znacznika zdarzenia](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Znacznik zdarzenia zdefiniowane przez użytkownika<br /> Oznacza określonej lokalizacji, zgodnie z definicją w aplikacji.|

## <a name="marking-user-defined-events-in-your-app"></a>Oznaczanie zdarzeń zdefiniowanych przez użytkownika w aplikacji
 Zdarzenia zdefiniowane przez użytkownika są specyficzne dla aplikacji. Ich umożliwia korelowanie istotne zdarzenia, które wystąpiły w aplikacji za pomocą zdarzeń na liście zdarzeń grafiki. Na przykład można utworzyć grupy zdarzeń zdefiniowanych przez użytkownika w celu uporządkowania zdarzeń powiązanych — takich jak te, które renderują interfejsu użytkownika — na grupy i hierarchie są tak, aby łatwiej przeglądać listę zdarzeń, lub możesz utworzyć znaczniki, gdy niektóre rodzaje obiektów rysowany tak, aby można łatwo znaleźć listy zdarzeń ich zdarzenia grafiki.

 Aby utworzyć grupy i znaczników w swojej aplikacji, należy użyć tych samych interfejsów API, który program Direct3D oferuje do użytku przez inne Direct3D, narzędzia debugowania. Te interfejsy API czasami się zmieniać między wersjami programu Direct3D, ale podstawowa funkcjonalność jest taka sama.

### <a name="user-defined-events-in-direct3d-12"></a>Zdarzeń zdefiniowanych przez użytkownika w Direct3D 12
 Aby utworzyć grupy i znaczników w Direct3D 12, przy użyciu interfejsów API, opisane w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, które można użyć w zależności od tego, czy są oznaczanie zdarzeń w kolejce poleceń, czy polecenie listy.

|Opis interfejsu API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Sprawdź dostępność zdarzenie zdefiniowane przez użytkownika|[PIXGetStatus](https://msdn.microsoft.com/library/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](https://msdn.microsoft.com/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|
|Rozpocznij grupy zdarzeń|[PIXBeginEvent](https://msdn.microsoft.com/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](https://msdn.microsoft.com/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|
|W końcu grupy zdarzeń|[PIXEndEvent](https://msdn.microsoft.com/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](https://msdn.microsoft.com/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|
|Utwórz — znacznik zdarzenia|[PIXSetMarker](https://msdn.microsoft.com/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](https://msdn.microsoft.com/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Zdarzenia zdefiniowane przez użytkownika w programie Direct3D 11 i jego starszych wersji
 Aby utworzyć grupy i znaczniki w interfejsie Direct3D 11 lub wcześniej, przy użyciu interfejsów API, opisane w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, które służy do różnych wersji programu Direct3D 11 i starszych wersji Direct3D.

|Opis interfejsu API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|Rodzina D3DPerf_ interfejsu API (Direct3D 11.0 i starsze)|
|---------------------| - | - | - |
|Rozpocznij grupy zdarzeń|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|W końcu grupy zdarzeń|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Utwórz — znacznik zdarzenia|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Można użyć dowolnego z tych interfejsów API, które obsługuje daną wersję programu Direct3D — na przykład, jeśli są przeznaczone dla interfejsu API Direct3D 11.1, możesz użyć albo `SetMarker` lub `D3DPerf_SetMarker` utworzyć znacznika zdarzenia, ale nie `SetMarkerInt` ponieważ jej dostępność tylko w Direct3D 11.2 — a nawet można łączyć te, które obsługują różne wersje programu Direct3D ze sobą w tej samej aplikacji.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historia zasobów
Visual Studio 2017 i większa zawierają **Historia zasobów** okna.  Wybierając ikonę Obejrzyj ![ikona monitorowania](media/gfx_watch.png) obok wpisu w **listy zdarzeń** oknie zostanie wyświetlone okno **Historia zasobów** okna, które przedstawiono poniżej:

![Historia zasobów](media/gfx_diag_resource_history.png)

To okno służy do wyświetlania historii elementu wybranego na liście zdarzeń.  Lista rozwijana u góry, można wybrać inne elementy, aby wyświetlić historię.  W górnej połowie okna zawiera **zdarzenia konfiguracji klatki**.  Są to zdarzenia, które można podzielić na *Utwórz* wpisz kategorię i wywołań, które zwykle inicjowania i Utwórz zasób.  Dolnej części okna zawiera **zdarzenia klatki** sekcji.  Te są normalne odczytu i zapisu zdarzenia, które wystąpiły w czasie korzystania z zasobów.

| Kolumna | Opis |
|-----------| - |
| **Typ** | Zazwyczaj zawiera typ wpisu *Utwórz*, *odczytu* i *zapisu*. |
| **Widok** | Pokazuje Miniatura zasobu w tej chwili czasu.  Dwukrotnie kliknij miniaturę, aby otworzyć widok szczegółów zasobów w tym czasie. |
| **Event** | Pokazuje wywołanie metody, które wystąpiły, który wygenerował zdarzenie.  Wszelkie dodatkowe historię na poszczególne elementy można wyświetlić, wybierając ikonę Obejrzyj ![ikona monitorowania](media/gfx_watch.png) odpowiedniego wiersza.  Ponadto dowolnego elementu, który jest rysowana w kolorze niebieskim, takich jak `m_commandList` na powyższym zrzucie ekranu, można wybrać Aby uzyskać więcej informacji. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)