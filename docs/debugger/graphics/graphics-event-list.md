---
title: Lista zdarzeń grafiki | Microsoft Docs
description: Użyj listy zdarzeń grafiki w analizator grafiki programu Visual Studio, aby eksplorować zdarzenia Direct3D, które zostały zarejestrowane podczas renderowania ramki gry lub aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c964cda5cbe2903cf9511659b9a8f9bfb9f4aad6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884523"
---
# <a name="graphics-event-list"></a>Lista zdarzeń grafiki
Użyj listy zdarzeń grafiki w analizator grafiki programu Visual Studio, aby eksplorować zdarzenia Direct3D, które zostały zarejestrowane podczas renderowania ramki gry lub aplikacji.

 Jest to lista zdarzeń:

 ![Lista zdarzeń o nazwie "index".](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Korzystanie z listy zdarzeń
 Po wybraniu zdarzenia na liście zdarzeń zostanie ono odzwierciedlone w informacjach wyświetlanych przez inne narzędzia do analizy grafiki; Korzystając z listy zdarzeń w połączeniu z tymi innymi narzędziami, można szczegółowo sprawdzić problem z renderowaniem w celu ustalenia jego przyczyny. Aby dowiedzieć się więcej o sposobach rozwiązywania problemów z renderowaniem przy użyciu listy zdarzeń wraz z innymi narzędziami do analizy grafiki, zobacz [przykłady](graphics-diagnostics-examples.md).

 Efektywne korzystanie z funkcji listy zdarzeń jest ważne dla zaawansowania ramek, które mogą zawierać tysiące zdarzeń. Aby efektywnie korzystać z listy zdarzeń, wybierz widok najlepiej sprawdza się dla Ciebie, użyj wyszukiwania do filtrowania listy zdarzeń, postępuj zgodnie z linkami, aby dowiedzieć się więcej na temat obiektów Direct3D, które są skojarzone ze zdarzeniem, i użyj przycisków strzałek, aby szybko przełączać się między wywołaniami rysowania.

### <a name="color-coded-events-in-direct3d-12"></a>Zdarzenia kodowane kolorem w programie Direct3D 12
 Direct3D 12 uwidacznia wiele kolejek, które odpowiadają różnym funkcjom sprzętowym. Aby ułatwić zidentyfikowanie kolejki skojarzonej z konkretnym zdarzeniem grafiki w programie Direct3D 12, zdarzenia są kodowane kolorami na liście zdarzeń zgodnie z ich kolejką podczas pracy z funkcją przechwytywania aplikacji Direct3D 12.

|Kolejka Direct3D|Kolor|
|-----------------------|-----------|
|Kolejka renderowania|Green (Zielony)|
|Kolejka obliczeń|Yellow|
|Kopiuj kolejkę|Orange|

 Program Direct3D 11 nie uwidacznia wielu kolejek, dlatego zdarzenia nie są kodowane na liście zdarzeń podczas pracy z funkcją przechwytywania aplikacji Direct3D 11.

### <a name="event-list-views"></a>Widoki listy zdarzeń
 Lista zdarzeń obsługuje dwa różne widoki, które organizują zdarzenia grafiki na różne sposoby obsługi przepływu pracy i preferencji. Pierwszy widok to *Widok pracy procesora GPU* , który organizuje zdarzenia i ich stan skojarzony hierarchicznie. Drugi widok to *Widok osi czasu* , który organizuje zdarzenia chronologicznie, na płaskiej liście.

 W widoku **roboczym procesora GPU** są wyświetlane przechwycone zdarzenia i ich stan w hierarchii. Najwyższego poziomu hierarchii składają się z zdarzeń, takich jak wywołania rysowania, czyszczenia, obecności i tych, które są związane z widokami. Na liście zdarzeń można rozwinąć wywołania rysowania, aby wyświetlić stan urządzenia, który był aktualny w momencie wywołania remisu; można również rozszerzyć każdy rodzaj stanu, aby wyświetlić zdarzenia ustawiające ich wartości. Na tym poziomie można także sprawdzić, czy określony stan został ustawiony w poprzedniej klatce lub czy został ustawiony więcej niż jeden raz od ostatniego wywołania rysowania.

 Widok **oś czasu** wyświetla każde przechwycone zdarzenie w kolejności chronologicznej. Ten sposób organizowania listy zdarzeń jest taki sam jak w poprzednich wersjach programu Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Aby zmienić tryb widoku listy zdarzeń

- W oknie **Lista zdarzeń grafiki** , powyżej listy zdarzeń, zlokalizuj listę rozwijaną **Widok** i wybierz widok **oś czasu** lub widok **pracy procesora GPU** .

### <a name="filtering-events"></a>Filtrowanie zdarzeń
 Możesz użyć pola wyszukiwania — znajdującego się w prawym górnym rogu okna **Lista zdarzeń grafiki** — aby przefiltrować listę zdarzeń w celu uwzględnienia tylko zdarzeń, których nazwy zawierają określone słowa kluczowe. Możesz określić pojedyncze słowa kluczowe, takie jak `Vertex` pokazano na poprzedniej ilustracji — lub kilka słów kluczowych przy użyciu listy rozdzielanej średnikami, na przykład `Draw;Primitive` , która jest zgodna ze zdarzeniami, które mają `Draw` `Primitive` nazwę lub. Wyszukiwania są wrażliwe na odstępy — na przykład `VSSet` i `VS Set` są różnymi wyszukiwaniami — dlatego należy uważnie sprawdzać przeszukiwanie.

### <a name="moving-between-draw-calls"></a>Przechodzenie między wywołaniami rysowania
 Ponieważ badanie `Draw` wywołań jest szczególnie ważne, można użyć **przejść do następnego wywołania rysowania** i **przejść do poprzedniego przycisku rysowania wywołania** — znajdującego się w lewym górnym rogu okna **Lista zdarzeń grafiki** — w celu szybkiego znalezienia i przechodzenia między wywołaniami rysowania.

### <a name="links-to-graphics-objects"></a>Linki do obiektów graficznych
 W celu zrozumienia pewnych zdarzeń graficznych mogą być potrzebne dodatkowe informacje o bieżącym stanie Direct3D lub obiektów Direct3D, do których odwołuje się zdarzenie. Wiele zdarzeń zawiera linki do tych informacji, które można wykonać, aby uzyskać więcej szczegółów.

## <a name="kinds-of-events-and-event-markers"></a>Rodzaje zdarzeń i znaczniki zdarzeń
 Zdarzenia, które są wyświetlane na liście zdarzeń, są zorganizowane w cztery kategorie: zdarzenia ogólne, narysuj zdarzenia, zdefiniowane przez użytkownika grupy zdarzeń i znaczniki zdarzeń zdefiniowane przez użytkownika. Z wyjątkiem ogólnych zdarzeń każde zdarzenie jest wyświetlane wraz z ikoną wskazującą kategorię, do której należy.

|Ikona|Opis zdarzenia|
|----------|-----------------------|
|(brak ikony)|Zdarzenie ogólne<br /> Każde zdarzenie, które nie jest zdarzeniem zdefiniowanym przez użytkownika, grupą zdarzeń zdefiniowanym przez użytkownika lub zdarzeniem remisu.|
|![Ikona zdarzenia rysowania](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Rysuj wydarzenie<br /> Oznacza zdarzenie rysowania, które wystąpiło w przechwyconej ramce.|
|![Ikona znacznika zdarzenia zdefiniowanego przez użytkownika&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Grupa zdarzeń zdefiniowana przez użytkownika<br /> Grupuje zdarzenia pokrewne zdefiniowane przez aplikację.|
|![Ikona znacznika zdarzenia zdefiniowanego przez użytkownika&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Znacznik zdarzenia zdefiniowany przez użytkownika<br /> Oznacza określoną lokalizację zdefiniowaną przez aplikację.|

## <a name="marking-user-defined-events-in-your-app"></a>Oznaczanie zdarzeń zdefiniowanych przez użytkownika w aplikacji
 Zdarzenia zdefiniowane przez użytkownika są specyficzne dla Twojej aplikacji. Można ich użyć do skorelowania poważnych zdarzeń występujących w aplikacji ze zdarzeniami na liście zdarzeń grafiki. Można na przykład utworzyć grupy zdarzeń zdefiniowane przez użytkownika, aby organizować powiązane zdarzenia, takie jak te, które renderują interfejs użytkownika w grupach lub hierarchiach, dzięki czemu można łatwiej przeglądać listę zdarzeń. można też tworzyć znaczniki, gdy są rysowane określone rodzaje obiektów, dzięki czemu można łatwo znaleźć na liście zdarzeń swoje zdarzenia graficzne.

 Aby utworzyć grupy i znaczniki w aplikacji, należy użyć tych samych interfejsów API, które są dostępne dla innych narzędzi debugowania Direct3D przez program Direct3D. Te interfejsy API czasami zmieniają się między wersjami programu Direct3D, ale podstawowe funkcje są takie same.

### <a name="user-defined-events-in-direct3d-12"></a>Zdarzenia zdefiniowane przez użytkownika w programie Direct3D 12
 Aby utworzyć grupy i znaczniki w programie Direct3D 12, Użyj interfejsów API opisanych w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, których można użyć w zależności od tego, czy oznaczasz zdarzenia w kolejce poleceń, czy na liście poleceń.

|Opis interfejsu API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Sprawdź dostępność zdarzeń zdefiniowanych przez użytkownika|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Rozpocznij pracę grupy zdarzeń|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Zakończ grupę zdarzeń|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Tworzenie znacznika zdarzenia|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Zdarzenia zdefiniowane przez użytkownika w programie Direct3D 11 i starszych wersjach
 Aby utworzyć grupy i znaczniki w programie Direct3D 11 lub starszym, Użyj interfejsów API opisanych w tej sekcji. Poniższa tabela zawiera podsumowanie interfejsów API, których można użyć dla różnych wersji programu Direct3D 11 i starszych wersji programu Direct3D.

|Opis interfejsu API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11,2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11,1)|Rodzina interfejsów API D3DPerf_ (Direct3D 11,0 i starsze)|
|---------------------| - | - | - |
|Rozpocznij pracę grupy zdarzeń|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Zakończ grupę zdarzeń|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Tworzenie znacznika zdarzenia|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Możesz użyć dowolnego z tych interfejsów API, które obsługuje wersja Direct3D — na przykład, jeśli korzystasz z interfejsu API programu Direct3D 11,1, możesz użyć albo `SetMarker` `D3DPerf_SetMarker` , aby utworzyć znacznik zdarzenia, ale nie jest on `SetMarkerInt` dostępny tylko w programie Direct3D 11.2 — i można nawet mieszać te, które obsługują różne wersje programu Direct3D razem w tej samej aplikacji.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historia zasobów
Program Visual Studio 2017 lub nowszy zawiera okno **historia zasobów** .  Wybranie ikony czujki ![ Obserwuj ](media/gfx_watch.png) obok pozycji w oknie **Lista zdarzeń** spowoduje wyświetlenie okna **historii zasobów** wyświetlonego poniżej:

![Historia zasobów](media/gfx_diag_resource_history.png)

To okno umożliwia wyświetlenie historii wybranego elementu na liście zdarzeń.  Lista rozwijana u góry może służyć do wybierania innych elementów w celu wyświetlenia historii.  Górna połowa okna zawiera **zdarzenia konfiguracji klatki**.  Są to zdarzenia, które znajdują się w kategorii *Create* Type i są wywołaniami, które zazwyczaj inicjują i tworzą zasób.  Dolna połowa okna zawiera sekcję **zdarzenia ramki** .  Są to normalne zdarzenia odczytu i zapisu występujące podczas korzystania z zasobu.

| Kolumna | Opis |
|-----------| - |
| **Typ** | Pokazuje typ wpisu, zazwyczaj *Tworzenie*, *Odczyt* i *zapis*. |
| **Wyświetlanie** | Pokazuje w tym momencie miniaturę zasobu.  Kliknij dwukrotnie miniaturę, aby otworzyć w tym momencie widok szczegółów zasobu. |
| **Zdarzenie** | Pokazuje wywołanie metody, które wygenerowało zdarzenie.  Każdą dodatkową historię poszczególnych elementów można wyświetlić, wybierając ikonę czujki Obejrzyj ikonę ![ Obserwuj ](media/gfx_watch.png) w odpowiednim wierszu.  Ponadto, `m_commandList` Aby uzyskać więcej szczegółów, można wybrać każdy element, który jest rysowany w niebieskim tekście, na przykład na poniższym zrzucie ekranu. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Zobacz też
- [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)