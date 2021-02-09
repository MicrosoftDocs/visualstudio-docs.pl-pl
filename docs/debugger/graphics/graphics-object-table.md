---
title: Tabela obiektów graficznych | Microsoft Docs
description: Dowiedz się więcej na temat tabeli obiektów graficznych, która w analizie grafiki programu Visual Studio ułatwia zrozumienie obiektów Direct3D, które obsługują ramkę gry lub aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095828e711f860662432edd767b19493b73c56c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887578"
---
# <a name="graphics-object-table"></a>Tabela obiektów graficznych
Tabela obiektów graficznych w analizie grafiki programu Visual Studio ułatwia zrozumienie obiektów Direct3D, które obsługują ramkę gry lub aplikacji.

 Jest to tabela obiektów:

 ![Obiekty Direct3D, które zostały utworzone przez aplikację.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>Zrozumienie tabeli obiektów graficznych
 Za pomocą tabeli obiektów można analizować obiekty Direct3D, które obsługują renderowanie określonej ramki. Problem z renderowaniem można zlokalizować do określonego obiektu, sprawdzając jego właściwości i dane (przy użyciu innych narzędzi Diagnostyka grafiki wcześniej w diagnostyce, można zawęzić listę obiektów, które mogą nie być oczekiwane.) Po znalezieniu poprawnego obiektu można użyć wizualizacji, który jest specyficzny dla jego typu, aby go sprawdzić — na przykład można użyć edytora obrazów do wyświetlania tekstury lub *wizualizatora bufora* , aby wyświetlić zawartość bufora.

 Tabela obiektów obsługuje kopiowanie i wklejanie, aby można było użyć innego narzędzia — na przykład programu Microsoft Excel — do badania jego zawartości.

 Ponadto można użyć listy rozwijanej **Typ** w lewym górnym rogu, aby przełączyć obiekty typu **bufory**, programy do **cieniowania** lub **tekstury** lub wszystkie te elementy jednocześnie.  Ponadto możesz użyć pola wyszukiwania w prawym górnym rogu, aby znaleźć określone wiersze dla wszystkich prezentowanych danych.  Można na przykład wyszukać *D32_FLOAT* , aby znaleźć na liście wszystkie wystąpienia obiektów tego formatu.

### <a name="graphics-object-table-format"></a>Format tabeli obiektów graficznych
 W tabeli obiektów są wyświetlane obiekty i zasoby Direct3D, które obsługują ramkę, która jest skojarzona z wybranym zdarzeniem — na przykład obiekty stanu, bufory, cieniowanie, tekstury i inne zasoby. Obiekty, które zostały utworzone w poprzedniej klatce, ale nie są używane w przechwyconej ramce, są pomijane w tabeli obiektów. Obiekty, które zostały zniszczone przez poprzednie zdarzenia w przechwyconej ramce, są pomijane w kolejnych zdarzeniach. Obiekty, które nie są ustawione na D3D10Device lub D3D11DeviceContext są wyświetlane jako szary tekst. Obiekty są wyświetlane w formacie tabeli.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator**|Identyfikator obiektu.|
|**Nazwa**|Informacje specyficzne dla aplikacji, które zostały ustawione dla obiektu za pomocą funkcji Direct3D `SetPrivateData` — zwykle do dostarczania dodatkowych informacji identyfikujących obiekt.|
|**Typ**|Typ obiektu.|
|**Aktywny**|Wyświetla wartość "*" dla obiektu, który został ustawiony w D3D10Device lub D3D11DeviceContext w przechwyconej ramce.<br /><br /> Odnosi się to do obiektów, które są wyświetlane w postaci szarego tekstu, ale zawiera wpis kolumny, którego można użyć w celu sortowania tabeli obiektów.|
|**Rozmiar**|Rozmiar obiektu w bajtach.|
|**Format**|Format obiektu. Na przykład format obiektu tekstury lub model cieniowania obiektu cieniowania.|
|**Width**|Szerokość obiektu tekstury. Nie dotyczy innych typów obiektów.|
|**Height**|Wysokość obiektu tekstury. Nie dotyczy innych typów obiektów.|
|**Ścisł**|Głębokość obiektu tekstury trójwymiarowej. Jeśli teksturą nie jest 3-D, wówczas wartość jest równa 0. Nie dotyczy innych typów obiektów.|
|**MIPS**|Liczba poziomów MIP, które ma obiekt tekstury. Nie dotyczy innych typów obiektów.|
|**Rozmiaru tablicy**|Liczba tekstur w tablicy tekstury. Zakres jest z przedziału od 1 do górnej granicy zdefiniowanej przez bieżący poziom funkcji. W przypadku mapy modułu ta wartość jest 6 razy większa od liczby map modułów w tablicy.|
|**Samples**|Liczba próbek na piksel.|

## <a name="graphics-object-viewers"></a>Przeglądarki obiektów graficznych
 Aby wyświetlić szczegóły dotyczące obiektu, otwórz go, wybierając jego nazwę w tabeli obiektów. Szczegóły dotyczące obiektu są wyświetlane w różnych formatach, w zależności od typu obiektu. Na przykład tekstury są wyświetlane przy użyciu przeglądarki tekstury i stanu urządzenia, takich jak kontekst urządzenia D3D11, jest wyświetlany jako sformatowana lista. Różne wersje programu Direct3D korzystają z różnych obiektów, a często charakterystyczne Wizualizatory dla najważniejszych obiektów każdej wersji.

 Oto podgląd tekstury przedstawiający zawartość etapu potoku tworzenia danych wyjściowych.

 ![Wersja zapoznawcza tekstury wyświetlającej scalanie danych wyjściowych](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>Lista poleceń D3D12
 W programie Direct3D 12 lista poleceń jest obiektem, który rejestruje polecenia w programie przydzielania poleceń, dzięki czemu mogą one być przesyłane do procesora GPU jako pojedyncze żądanie. Lista poleceń zazwyczaj wykonuje szereg poleceń tworzenia stanu, rysowania, czyszczenia i kopiowania. Są one szczególnie ważne, ponieważ są one preferowanymi metodami renderowania w programie Direct3D 12 i mogą być ponownie używane między ramkami, aby zwiększyć wydajność. Szczegóły listy poleceń są wyświetlane w nowym oknie dokumentu z informacjami związanymi z każdym etapem potoku przedstawionym na jego własnej karcie.

### <a name="d3d12-pipeline-state-object-pso"></a>Obiekt stanu potoku D3D12 (PSO)
 W programie Direct3D 12 obiekt stanu potoku reprezentuje znaczną część stanu procesora GPU, włącznie z aktualnie ustawionymi cieniami i niektórymi obiektami stanu stałej funkcji. Po utworzeniu obiekt stanu potoku jest niezmienny — aplikacja może zmienić konfigurację potoku przez powiązanie innego obiektu stanu potoku. Szczegóły obiektu PSO są wyświetlane w nowym oknie dokumentu z szczegółowymi informacjami o konfiguracji potoku.

### <a name="d3d12-root-signature"></a>D3D12 podpis główny
 W programie Direct3D 12 podpis główny definiuje wszystkie zasoby, które są powiązane z potokiem grafiki lub obliczeń, i łączy z listami poleceń do zasobów wymaganych przez program do cieniowania. Zwykle istnieje jeden podpis główny dla grafiki i jeden do obliczeń w aplikacji. Szczegóły podpisu głównego są wyświetlane w nowym oknie dokumentu, z szczegółowymi informacjami o podpisie głównym, które są ułożone hierarchicznie.

### <a name="d3d12-resources"></a>Zasoby D3D12
 W programie Direct3D 12 zasoby są odporne na wszystkie obiekty, które dostarczają dane do potoku renderowania. jest to w przeciwieństwie do Direct3D11, które definiuje wiele konkretnych obiektów dla różnych rodzajów zasobów i wymiarów. Zasób Direct3D 12 może zawierać dane tekstury, dane wierzchołków, dane programu do cieniowania i inne elementy — mogą nawet reprezentować cele renderowania, takie jak bufor głębokości. Szczegóły zasobu Direct3D 12 są wyświetlane w nowym oknie dokumentu; Analiza grafiki będzie używać odpowiedniej przeglądarki dla zawartości obiektu zasobu, jeśli jest w stanie określić jej typ. Na przykład obiekt zasobu, który zawiera dane tekstury, jest wyświetlany przy użyciu przeglądarki tekstury, podobnie jak obiekt D3D11 Texture2D.

### <a name="device-context-object"></a>Obiekt kontekstu urządzenia
 W programie Direct3D 11 i Direct3D 10 obiekt kontekstu urządzenia (**d3d11 Device Context** lub **d3d10 Device**) jest szczególnie istotny, ponieważ zawiera najważniejsze informacje o stanie i łączy się z innymi aktualnie ustawionymi obiektami stanu. Szczegóły kontekstu urządzenia są wyświetlane w nowym oknie dokumentu, a każda kategoria informacji jest prezentowana na własnej karcie. Kontekst urządzenia zmienia się po wybraniu nowego zdarzenia w celu odzwierciedlenia bieżącego stanu urządzenia.

### <a name="buffer-object"></a>Obiekt buforu
 Szczegóły obiektu buforu (bufor D3D11 lub bufor D3D10) są wyświetlane w nowym oknie dokumentu, które przedstawia zawartość buforu w tabeli i udostępnia interfejs do zmiany sposobu wyświetlania zawartości buforu. Tabela **danych buforu** obsługuje kopiowanie i wklejanie, aby można było użyć innego narzędzia — na przykład Microsoft Excel — do badania jego zawartości. Zawartość buforu jest interpretowana zgodnie z wartością pola kombi **Format** , która znajduje się powyżej tabeli **danych buforu** . W polu można wprowadzić złożony format danych składający się z typów danych, które są wymienione w poniższej tabeli. Na przykład "float int" wyświetla listę struktur, które zawierają 32-bitową wartość zmiennoprzecinkową, a następnie 32-bitową wartość całkowitą ze znakiem. Złożone formaty danych, które zostały określone, są dodawane do pola kombi do późniejszego użycia.

 Możesz również przełączać pole wyboru **Pokaż przesunięcia** , aby ukryć lub wyświetlić przesunięcie każdego elementu w buforze.

|Typ|Opis|
|----------|-----------------|
|**liczba zmiennoprzecinkowa**|32-bitowa wartość zmiennoprzecinkowa.|
|**float2**|Wektor, który zawiera 2 32-bitowe wartości zmiennoprzecinkowe.|
|**float3**|Wektor, który zawiera 3 32-bitowe wartości zmiennoprzecinkowe.|
|**float4**|Wektor, który zawiera 4 32-bitowe wartości zmiennoprzecinkowe.|
|**Bajc**|8-bitowa liczba całkowita ze znakiem.|
|**2byte**|16-bitowa liczba całkowita ze znakiem.|
|**4byte**|32-bitowa liczba całkowita ze znakiem. Wartość taka sama jak **int**.|
|**8byte**|64-bitowa liczba całkowita ze znakiem. Taka sama jak **Int64**.|
|**xbyte**|8-bitowa wartość szesnastkowa.|
|**x2byte**|16-bitowa wartość szesnastkowa.|
|**x4byte**|32-bitowa wartość szesnastkowa. Analogicznie jak **xint**.|
|**x8byte**|64-bitowa wartość szesnastkowa. Analogicznie jak **xint64**.|
|**ubyte**|8-bitowa liczba całkowita bez znaku.|
|**u2byte**|16-bitowa liczba całkowita bez znaku.|
|**u4byte**|32-bitowa liczba całkowita bez znaku. Analogicznie jak **uint**.|
|**u8byte**|64-bitowa liczba całkowita bez znaku. Analogicznie jak **UInt64**.|
|**Half**|16-bitowa wartość zmiennoprzecinkowa.|
|**half2**|Wektor, który zawiera 2 16-bitowe wartości zmiennoprzecinkowe.|
|**half3**|Wektor, który zawiera 3 16-bitowe wartości zmiennoprzecinkowe.|
|**half4**|Wektor, który zawiera 4 16-bitowe wartości zmiennoprzecinkowe.|
|**liczba o podwójnej precyzji**|64-bitowa wartość zmiennoprzecinkowa.|
|**int**|32-bitowa liczba całkowita ze znakiem. Analogicznie jak **4byte**.|
|**Int64**|64-bitowa liczba całkowita ze znakiem. Analogicznie jak **8byte**.|
|**xint**|32-bitowa wartość szesnastkowa. Analogicznie jak **x4byte**.|
|**xint64**|64-bitowa wartość szesnastkowa. Analogicznie jak **x8byte**.|
|**uint**|32-bitowa liczba całkowita bez znaku. Analogicznie jak **u4byte**.|
|**UInt64**|64-bitowa liczba całkowita bez znaku. Analogicznie jak **u8byte**.|
|**bool**|Wartość logiczna ( `true` lub `false` ). Każda wartość logiczna jest reprezentowana przez 32-bitową wartość.|

## <a name="see-also"></a>Zobacz też
- [Diagnostyka grafiki (debugowanie grafiki DirectX)](visual-studio-graphics-diagnostics.md)
- [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)