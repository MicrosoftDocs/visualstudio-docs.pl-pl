---
title: Tabela obiektów graficznych | Dokumentacja firmy Microsoft
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
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba3ce8aa0727471ff4385792d85659fa2d208dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809093"
---
# <a name="graphics-object-table"></a>Tabela obiektów graficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tabela obiektów graficznych w analizy grafiki w usłudze Visual Studio pomaga zrozumieć obiekty Direct3D, które obsługują ramki grach i aplikacjach.  
  
 Jest to tabela obiektów:  
  
 ![Obiekty Direct3D, które zostały utworzone przez aplikację.](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Opis tabeli obiektów grafiki  
 Za pomocą tabeli obiektów, można analizować obiekty Direct3D, obsługujące renderowania określoną ramkę. Można wyznaczyć z problemem renderowania do określonego obiektu, sprawdzając jej właściwości i danych (przy użyciu innych narzędzi diagnostyki grafiki we wcześniejszej części usługi Diagnostyka, można ograniczyć listę obiektów, które mogą nie być, czego oczekiwać.) Po znalezieniu obiekt powodujący problemy, można użyć wizualizacji, które są specyficzne dla jego typu, aby zbadać jego — na przykład służy Edytor obrazów do wyświetlania tekstury, lub *Wizualizator buforu* można wyświetlić zawartości buforu.  
  
 Tabela obiektów obsługuje kopiowania i wklejania, dzięki czemu można użyć innego narzędzia — na przykład program Microsoft Excel — aby zbadać jego zawartość.  
  
### <a name="graphics-object-table-format"></a>Format tabeli obiektów grafiki  
 Tabela obiektów wyświetla obiekty Direct3D i zasobów, które obsługują ramkę, która jest skojarzona z wybranego zdarzenia — na przykład stan obiektów, buforów, programów do cieniowania, tekstury i inne zasoby. Obiekty, które zostały utworzone w poprzedniej ramki, ale nie są używane podczas przechwyconej ramki zostały pominięte w tabeli obiektów. Obiekty, które zostały zniszczone przez poprzednie zdarzenia podczas przechwyconej klatce są pomijane w ramach kolejnych zdarzeń. Obiekty, które nie są ustawione na D3D10Device lub D3D11DeviceContext są wyświetlane jako szary tekst. Obiekty są wyświetlane w formacie tabeli.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator**|Identyfikator obiektu.|  
|**Nazwa**|Informacje specyficzne dla aplikacji, która została ustawiona na obiekt za pomocą funkcji programu Direct3D `SetPrivateData`— zwykle podać dodatkowe informacje identyfikacyjne dotyczące obiektu.|  
|**Typ**|Typ obiektu.|  
|**Aktywne**|Wyświetla "*" dla obiektu, który został ustawiony na D3D10Device lub D3D11DeviceContext podczas przechwyconej ramki.<br /><br /> Odnosi się do obiektów, które są wyświetlane jako szary tekst, ale zawiera wpis kolumn, który można użyć, aby ułatwić sortowanie tabeli obiektów.|  
|**Rozmiar**|Rozmiar obiektu w bajtach.|  
|**Format**|Format obiektu. Na przykład format obiektu tekstury lub cieniowania modelu obiektu programu do cieniowania.|  
|**Szerokość**|Szerokość obiektu tekstury. Nie ma zastosowania do innych obiektów.|  
|**Wysokość**|Wysokość obiektu tekstury. Nie ma zastosowania do innych obiektów.|  
|**Głębokość**|Głębokość obiektu tekstury 3-D. Jeśli tekstura nie jest 3-w, wartość wynosi 0. Nie ma zastosowania do innych obiektów.|  
|**MIPS**|Liczba poziomów Mipmapy, które ma obiekt tekstury. Nie ma zastosowania do innych obiektów.|  
|**Rozmiaru tablicy**|Liczba tekstury w tablicy tekstury. Zakres jest z zakresu od 1 do zdefiniowanych przez bieżący poziom funkcji górną granicę. Dla mapy modułu ta wartość jest 6-krotnością liczby map modułu w tablicy.|  
|**Przykłady**|Liczba multisamples na piksel.|  
  
## <a name="graphics-object-viewers"></a>Obiekt grafiki osoby przeglądające  
 Aby wyświetlić szczegóły dotyczące obiektu, należy go otworzyć, wybierając jego nazwę w tabeli obiektów. Szczegółowe informacje o obiekcie są wyświetlane w różnych formatach, w zależności od typu obiektu. Na przykład tekstury są wyświetlane przy użyciu przeglądarka tekstur i stan urządzenia, takie jak kontekst urządzenia D3D11 jest wyświetlany jako listę sformatowany. Różne wersje programu Direct3D, należy korzystać z różnych obiektów, a często są określone wizualizatorów najważniejszych obiektów w każdej wersji.  
  
 Oto przeglądarka tekstur, wyświetlanie zawartość etap potoku scalanie danych wyjściowych.  
  
 ![Podgląd tekstury, wyświetlanie scalanie danych wyjściowych](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Listy poleceń D3D12  
 W Direct3D 12 listy poleceń jest obiektem, który rejestruje polecenia do przydzielający polecenia, tak aby mogły one być przesyłane do procesora GPU jako pojedyncze żądanie. Listy poleceń zwykle wykonać szereg ustawienia stanu, rysowania, wyczyść i skopiuj polecenia. Są one szczególnie ważne, ponieważ jest preferowaną metodą renderowania w Direct3D 12 i może być ponownie wykorzystana między klatki, aby pomóc w zwiększeniu wydajności. Polecenie wyświetlić szczegółowe informacje są wyświetlane w nowym oknie dokumentu informacje związane z każdym etapie potoku przedstawione na osobnej karcie.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Obiekt stanu potoku D3D12 (PSO)  
 W Direct3D 12 obiekt stanu potoku reprezentuje znaczna część stan procesora GPU, w tym wszystkie obecnie zestaw programów do cieniowania i niektórych obiektów stan rozwiązany funkcji. Po utworzeniu obiektu stanu potoku jest niezmienny — aplikacji przez powiązanie obiektu stanu innym potoku można zmienić tylko konfiguracji potoku. PSO szczegóły są wyświetlane w nowym oknie dokumentu, szczegółowe informacje o konfiguracji potoku korzystanie hierarchicznie.  
  
### <a name="d3d12-root-signature"></a>Sygnatura główna D3D12  
 W Direct3D 12 sygnatura główna definiuje wszystkie zasoby, które są powiązane z potoku grafiki, czy obliczeń, a następnie łączy on listy poleceń do zasobów, które wymaga programów do cieniowania. Zazwyczaj ma jeden sygnatura główna grafiki i jeden dla zasobów obliczeniowych w aplikacji. Szczegóły podpisu główny są wyświetlane w nowym oknie dokumentu przy użyciu szczegółów sygnatury głównej korzystanie hierarchicznie.  
  
### <a name="d3d12-resources"></a>Zasoby D3D12  
 W Direct3D 12 zasobów są obiektów wychwytywania, które będą dostarczać dane do potoku renderowania; jest to w przeciwieństwie do Direct3D11, która zdefiniowana wiele obiektów określonych dla różnych typów i rozmiarów zasobów. Zasób Direct3D 12 może zawierać danych tekstury, danych wierzchołka, dane programu do cieniowania i — nawet reprezentują elementy docelowe renderowania, takich jak bufor głębokości. Szczegóły zasobu Direct3D 12 są wyświetlane w nowym oknie dokumentu; Analizy grafiki użyje przeglądarkę odpowiednią dla zawartości obiektu zasobu, jeśli jest w stanie określić jej typu. Na przykład obiekt zasobu, który zawiera dane tekstury jest wyświetlana przy użyciu przeglądarka tekstur podobnie jak obiekt D3D11 Texture2D jest.  
  
### <a name="device-context-object"></a>Obiekt kontekstu urządzenia  
 W Direct3D 11 i Direct3D 10 kontekstu urządzenia (**kontekstu urządzenia D3D11** lub **urządzeniem D3D10**) obiekt jest szczególnie ważne, ponieważ posiada najważniejsze informacje o stanie i łączy się on z innymi obiekty stanu, które są ustawione. Szczegóły kontekstu urządzenia są wyświetlane w nowym oknie dokumentu, a każda kategoria informacje są prezentowane istnieje na osobnej karcie. Zmiany kontekstu urządzenia po wybraniu nowe zdarzenie, aby odzwierciedlić bieżący stan urządzenia.  
  
### <a name="buffer-object"></a>Obiekt buforu  
 Szczegóły obiektu buforu (D3D11 buforu lub buforu D3D10) są wyświetlane w nowym oknie Dokument przedstawia informacje o zawartości buforu w tabeli, która udostępnia interfejs do zmiany sposobu wyświetlania zawartości buforu. **Buforować dane** tabeli obsługuje kopiowania i wklejania tak, aby użyć innego narzędzia — na przykład program Microsoft Excel — aby zbadać jego zawartość. Zawartość buforu jest interpretowane zgodnie z wartością **format** pola kombi, który znajduje się nad **buforować dane** tabeli. W polu można wprowadzić formatu danych złożony, który składa się z typów danych, które są wymienione w poniższej tabeli. Na przykład "float int" Wyświetla listę struktur, które zawierają wartość zmiennoprzecinkowa 32-bitowych następuje wartości 32-bitową. Formaty danych złożonych, które zostały określone przez są dodawane do pola kombi do późniejszego użycia.  
  
 Możesz się też przełączać **Pokaż przesunięcia** pole wyboru, aby ukryć lub wyświetlić przesunięcie każdego elementu w buforze.  
  
|Typ|Opis|  
|----------|-----------------|  
|**float**|Wartość zmiennoprzecinkowa 32-bitowych.|  
|**float2**|Wektor, zawierający dwie 32-bitowych wartości zmiennoprzecinkowych.|  
|**float3**|Wektor, zawierający trzy 32-bitowych wartości zmiennoprzecinkowych.|  
|**FLOAT4**|Wektor zawierający cztery 32-bitowych wartości zmiennoprzecinkowych.|  
|**byte**|Wartość liczby całkowitej ze znakiem 8-bitowych.|  
|**2 bajtów**|Wartość liczby całkowitej ze znakiem 16-bitowych.|  
|**4-bajtowych**|Wartość liczby całkowitej ze znakiem 32-bitowych. Taki sam jak **int**.|  
|**8 bajtów**|Wartość liczby całkowitej ze znakiem 64-bitowych. Taki sam jak **int64**.|  
|**xbyte**|8-bitową wartość szesnastkową.|  
|**x2byte**|16-bitową wartość szesnastkową.|  
|**x4byte**|32-bitową wartość szesnastkową. Taki sam jak **xint**.|  
|**x8byte**|64-bitowych wartość szesnastkową. Taki sam jak **xint64**.|  
|**ubyte**|Wartości 8-bitowej nieoznaczonej liczby całkowitej.|  
|**u2byte**|Wartość 16-bitowej nieoznaczonej liczby całkowitej.|  
|**u4byte**|Wartość 32-bitowej nieoznaczonej liczby całkowitej. Taki sam jak **uint**.|  
|**u8byte**|Wartość 64-bitowej nieoznaczonej liczby całkowitej. Taki sam jak **uint64**.|  
|**połowa**|16-bitowych wartości zmiennoprzecinkowych.|  
|**half2**|Wektor, zawierający dwie 16-bitowych wartości zmiennoprzecinkowych.|  
|**half3**|Wektor, zawierający trzy 16-bitowych wartości zmiennoprzecinkowych.|  
|**half4**|Wektor zawierający cztery 16-bitowych wartości zmiennoprzecinkowych.|  
|**double**|64-bitowych wartości zmiennoprzecinkowych.|  
|**int**|Wartość liczby całkowitej ze znakiem 32-bitowych. Taki sam jak **4-bajtowych**.|  
|**int64**|Wartość liczby całkowitej ze znakiem 64-bitowych. Taki sam jak **8 bajtów**.|  
|**xint**|32-bitową wartość szesnastkową. Taki sam jak **x4byte**.|  
|**xint64**|64-bitowych wartość szesnastkową. Taki sam jak **x8byte**.|  
|**uint**|Wartość 32-bitowej nieoznaczonej liczby całkowitej. Taki sam jak **u4byte**.|  
|**uint64**|Wartość 64-bitowej nieoznaczonej liczby całkowitej. Taki sam jak **u8byte**.|  
|**bool**|Wartość logiczna (`true` lub `false`) wartość. Każda wartość logiczna jest reprezentowany przez wartość 32-bitowa.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnostyka grafiki (debugowanie grafiki DirectX)](../debugger/visual-studio-graphics-diagnostics.md)   
 [Przewodnik: brak obiektów spowodowany stanem urządzenia](../debugger/walkthrough-missing-objects-due-to-device-state.md)



