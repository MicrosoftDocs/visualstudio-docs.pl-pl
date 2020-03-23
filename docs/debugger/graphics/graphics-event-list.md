---
title: Lista zdarzeń graficznych | Dokumenty firmy Microsoft
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
ms.openlocfilehash: d5c4e8f39ff77779985536e53d98ddc2785b109b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302127"
---
# <a name="graphics-event-list"></a>Lista zdarzeń grafiki
Lista zdarzeń grafiki w analizatorze grafiki programu Visual Studio umożliwia eksplorowanie zdarzeń Direct3D nagranych podczas renderowania ramki gry lub aplikacji.

 Oto lista zdarzeń:

 ![Lista zdarzeń, które mają "Indeks" w ich nazwie.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Korzystanie z listy zdarzeń
 Po wybraniu zdarzenia na liście zdarzeń jest ono odzwierciedlone w informacjach wyświetlanych przez inne narzędzia analizy grafiki; za pomocą listy zdarzeń w porozumieniu z tych innych narzędzi można zbadać problem renderowania szczegółowo, aby ustalić jego przyczynę. Aby dowiedzieć się więcej o tym, jak rozwiązać problemy z renderowaniem, korzystając z listy zdarzeń wraz z innymi narzędziami analizy grafiki, zobacz [Przykłady](graphics-diagnostics-examples.md).

 Korzystanie z funkcji listy zdarzeń skutecznie jest ważne dla poruszania się po złożonych ramek, które mogą zawierać tysiące zdarzeń. Aby skutecznie korzystać z listy zdarzeń, wybierz widok, który jest dla Ciebie najlepszy, użyj funkcji wyszukiwania do filtrowania listy zdarzeń, postępuj zgodnie z łączami, aby dowiedzieć się więcej o obiektach Direct3D skojarzonych ze zdarzeniem, a także użyć przycisków strzałek, aby szybko przechodzić między połączeniami rysowania.

### <a name="color-coded-events-in-direct3d-12"></a>Zdarzenia oznaczone kolorami w direct3D 12
 Direct3D 12 udostępnia wiele kolejek, które odpowiadają różnym funkcjom sprzętowym. Aby ułatwić identyfikację kolejki skojarzonej z określonym zdarzeniem graficznym w programie Direct3D 12, zdarzenia są oznaczone kolorami na liście zdarzeń zgodnie z ich kolejką podczas pracy z przechwytywaniem aplikacji Direct3D 12.

|Kolejka Direct3D 12|Kolor|
|-----------------------|-----------|
|Kolejka renderowania|Zielony|
|Kolejka obliczeń|Yellow|
|Kolejka kopiowania|Orange|

 Direct3D 11 nie udostępnia wielu kolejek, więc zdarzenia nie są oznaczone kolorami na liście zdarzeń podczas pracy z przechwytywaniem aplikacji Direct3D 11.

### <a name="event-list-views"></a>Widoki listy zdarzeń
 Lista zdarzeń obsługuje dwa różne widoki, które organizują zdarzenia graficzne na różne sposoby, aby obsługiwać przepływ pracy i preferencje. Pierwszy widok jest *widok pracy gpu,* który organizuje zdarzenia i ich stan skojarzony hierarchicznie. Drugi widok to *widok osi czasu,* który organizuje zdarzenia chronologicznie, na płaskiej liście.

 Widok **pracy gpu** wyświetla przechwycone zdarzenia i ich stan w hierarchii. Najwyższy poziom hierarchii składa się ze zdarzeń, takich jak wywołania rysowania, czyści, obecny i tych, które zajmują się widokami. Na liście zdarzeń można rozwinąć wywołania rysowania, aby wyświetlić stan urządzenia, który był aktualny w czasie wywołania rysowania; i można dalej rozszerzać każdy rodzaj stanu, aby wyświetlić zdarzenia, które ustawiają ich wartości. Na tym poziomie można również sprawdzić, czy określony stan został ustawiony w poprzedniej ramce lub czy został ustawiony więcej niż jeden raz od ostatniego wywołania rysowania.

 Widok **Oś czasu** Wyświetla każde przechwycone zdarzenie w porządku chronologicznym. Ten sposób organizowania listy zdarzeń jest taki sam jak w poprzednich wersjach programu Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Aby zmienić tryb widoku listy zdarzeń

- W oknie **Lista zdarzeń graficznych** nad listą zdarzeń znajdź listę rozwijana **Widok** i wybierz widok **osi czasu** lub widok **Praca gpu.**

### <a name="filtering-events"></a>Filtrowanie zdarzeń
 Za pomocą pola Wyszukiwania znajdującego się w prawym górnym rogu okna **Lista zdarzeń grafiki** można filtrować listę zdarzeń, aby uwzględnić tylko zdarzenia, których nazwy zawierają określone słowa kluczowe. Możesz określić pojedyncze `Vertex`słowa kluczowe, takie jak na poprzedniej ilustracji, lub wiele słów `Draw;Primitive`kluczowych, używając listy rozdzielanej średnikami, takiej jak — która pasuje do zdarzeń, które mają `Draw` lub `Primitive` w ich nazwach. Wyszukiwania są wrażliwe na odstępy `VSSet` `VS Set` — na przykład i są różne wyszukiwania — więc upewnij się, że wyszukiwanie jest dokładne.

### <a name="moving-between-draw-calls"></a>Przechodzenie między połączeniami rysowania
 Ponieważ badanie `Draw` połączeń jest szczególnie ważne, można użyć **połączenia Przejdź do następnego rysowania** i przejdź do poprzednich przycisków **wywołania rysowania** — znajdujących się w lewym górnym rogu okna **Lista zdarzeń grafiki** — aby szybko znajdować i przechodzić między połączeniami rysowania.

### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych
 Aby zrozumieć niektóre zdarzenia graficzne, może być konieczne dodatkowe informacje o bieżącym stanie Direct3D lub o obiektach Direct3D, do których odwołuje się zdarzenie. Wiele zdarzeń zawiera łącza do tych informacji, które można śledzić, aby uzyskać więcej szczegółów.

## <a name="kinds-of-events-and-event-markers"></a>Rodzaje zdarzeń i znaczniki zdarzeń
 Zdarzenia wyświetlane na liście zdarzeń są podzielone na cztery kategorie: zdarzenia ogólne, zdarzenia rysowania, grupy zdarzeń zdefiniowane przez użytkownika i znaczniki zdarzeń zdefiniowane przez użytkownika. Z wyjątkiem zdarzeń ogólnych, każde zdarzenie jest wyświetlane wraz z ikoną, która wskazuje kategorię, do której należy.

|Ikona|Opis zdarzenia|
|----------|-----------------------|
|(brak ikony)|Zdarzenie ogólne<br /> Każde zdarzenie, które nie jest zdarzeniem zdefiniowanym przez użytkownika, grupą zdarzeń zdefiniowaną przez użytkownika ani zdarzeniem rysowania.|
|![Ikona zdarzenia rysowania](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Zdarzenie rysowania<br /> Oznacza zdarzenie rysowania, które wystąpiło podczas przechwyconej ramki.|
|![Ikona znacznika zdarzeń zdefiniowana przez użytkownika&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Grupa zdarzeń zdefiniowana przez użytkownika<br /> Grupy powiązanych zdarzeń, zgodnie z definicją aplikacji.|
|![Ikona znacznika zdarzeń zdefiniowana przez użytkownika&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Znacznik zdarzenia zdefiniowany przez użytkownika<br /> Oznacza określoną lokalizację zdefiniowaną przez aplikację.|

## <a name="marking-user-defined-events-in-your-app"></a>Oznaczanie zdarzeń zdefiniowanych przez użytkownika w aplikacji
 Zdarzenia zdefiniowane przez użytkownika są specyficzne dla aplikacji. Można ich używać do skorelowania istotnych zdarzeń występujących w aplikacji ze zdarzeniami na liście zdarzeń grafiki. Można na przykład utworzyć zdefiniowane przez użytkownika grupy zdarzeń w celu organizowania powiązanych zdarzeń, takich jak te, które renderują interfejs użytkownika, w grupy lub hierarchie, aby łatwiej przeglądać listę zdarzeń, lub można tworzyć znaczniki, gdy określone rodzaje obiektów są tak, aby można było łatwo znaleźć ich zdarzenia graficzne na liście zdarzeń.

 Aby utworzyć grupy i znaczniki w aplikacji, należy użyć tych samych interfejsów API, które direct3D zapewnia do użycia przez inne narzędzia debugowania Direct3D. Te interfejsy API czasami zmieniają się między wersjami Direct3D, ale podstawowe funkcje są takie same.

### <a name="user-defined-events-in-direct3d-12"></a>Zdarzenia zdefiniowane przez użytkownika w direct3D 12
 Aby utworzyć grupy i znaczniki w direct3D 12, należy użyć interfejsów API opisanych w tej sekcji. W poniższej tabeli podsumowano interfejsy API, których można używać w zależności od tego, czy oznaczasz zdarzenia w kolejce poleceń, czy na liście poleceń.

|Opis interfejsu API|[ID3D12Kładekarz](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Sprawdzanie dostępności zdarzeń zdefiniowanych przez użytkownika|[PIXGetStatus (PIXGetStatus)](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus (PIXGetStatus)](/previous-versions//dn788637(v=vs.85))|
|Rozpoczynanie grupy zdarzeń|[PIXPowierzchnia](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXPowierzchnia](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Koń grupę zdarzeń|[PIXEndEvent (PIXEndEvent)](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent (PIXEndEvent)](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Tworzenie znacznika zdarzenia|[PIXSetMarker (PIXSetMarker)](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker (PIXSetMarker)](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Zdarzenia zdefiniowane przez użytkownika w direct3D 11 i wcześniejszych
 Aby utworzyć grupy i znaczniki w direct3D 11 lub starszym, użyj interfejsów API opisanych w tej sekcji. W poniższej tabeli podsumowano interfejsy API, których można używać w różnych wersjach direct3D 11 i wcześniejszych wersji direct3D.

|Opis interfejsu API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefiniowanaAnnocnia](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ rodziny INTERFEJSÓW API (Direct3D 11.0 i starsze)|
|---------------------| - | - | - |
|Rozpoczynanie grupy zdarzeń|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Koń grupę zdarzeń|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Tworzenie znacznika zdarzenia|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Można użyć dowolnego z tych interfejsów API obsługiwanych przez wersję Direct3D — na przykład, jeśli kierujesz interfejs API Direct3D 11.1, możesz użyć `SetMarker` lub `D3DPerf_SetMarker` utworzyć znacznik zdarzeń, ale nie `SetMarkerInt` dlatego, że jest on dostępny tylko w direct3D 11.2 — a nawet można mieszać te, które obsługują różne wersje Direct3D razem w tej samej aplikacji.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historia zasobów
Visual Studio 2017 i większa zawierają okno **Historia zasobów.**  Wybranie ikony ![](media/gfx_watch.png) zegarka obok wpisu w oknie **Lista zdarzeń** spowoduje wyświetlenie okna **Historia zasobów** pokazanego poniżej:

![Historia zasobów](media/gfx_diag_resource_history.png)

To okno umożliwia wyświetlanie historii wybranego elementu na liście zdarzeń.  Listy rozwijanej u góry mogą być używane do wybierania innych elementów, aby wyświetlić historię.  Górna połowa okna zawiera **zdarzenia konfiguracji ramki**.  Są to zdarzenia, które należą *do kategorii Utwórz* typ i są wywołania, które zazwyczaj inicjują i tworzą zasób.  Dolna połowa okna zawiera sekcję **Zdarzenia ramki.**  Są to normalne odczytu i zapisu zdarzenia, które występują podczas korzystania z zasobu.

| Kolumna | Opis |
|-----------| - |
| **Typ** | Pokazuje typ wpisu, zazwyczaj *Tworzenie*, *Odczyt* i *Zapis*. |
| **Widok** | Pokazuje miniaturę zasobu w tym momencie w czasie.  Kliknij dwukrotnie miniaturę, aby otworzyć widok szczegółów zasobu w tym czasie. |
| **Wydarzenie** | Pokazuje wywołanie metody, które wystąpiło, które wygenerowało zdarzenie.  Każdą dodatkową historię poszczególnych elementów można wyświetlić,](media/gfx_watch.png) wybierając ikonę zegarka ![w odpowiedniej linii.  Ponadto można wybrać dowolny element, który `m_commandList` jest rysowany niebieskim tekstem, na przykład na powyższym zrzucie ekranu, aby uzyskać więcej szczegółów. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Zobacz też
- [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)