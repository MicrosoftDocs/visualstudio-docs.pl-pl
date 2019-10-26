---
title: Okno dialogowe Ustawienia zaawansowane (Concurrency Visualizer) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa9d6658ae14c4b84aae9361f73e4701e758f975
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911219"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Okno dialogowe Ustawienia zaawansowane (Concurrency Visualizer)
Korzystając z okna dialogowego **Ustawienia zaawansowane** w wizualizatorze współbieżności, można kontrolować sposób zbierania śladów.  Okno dialogowe zawiera karty symboli, Tylko mój kod, buforowanie, filtrowanie, zdarzenia CLR, znaczniki, dostawcy i pliki.

## <a name="symbols"></a>Symbole
 Wizualizator współbieżności używa tych samych ustawień symboli co debuger programu Visual Studio. Wizualizator współbieżności używa ustawień do rozwiązywania stosów wywołań skojarzonych z danymi wydajności.  Podczas przetwarzania śladów, Wizualizator współbieżności uzyskuje dostęp do serwerów symboli, które są określone na stronie Ustawienia.  Gdy dostęp do tych danych odbywa się za pośrednictwem sieci, przetwarzanie śledzenia spowalnia się.  Aby skrócić czas wymagany do rozpoznawania symboli, można lokalnie buforować symbole. Jeśli symbole zostały pobrane, program Visual Studio załaduje je z lokalnej pamięci podręcznej.

## <a name="just-my-code"></a>Tylko mój kod
 Domyślnie Tylko mój kod jest zestawem. *exe* i. pliki *dll* , które są skojarzone z bieżącym rozwiązaniem w programie Visual Studio. Wizualizator współbieżności szacuje ten zestaw plików przy użyciu funkcji Tylko mój kod do filtrowania stosów wywołań. Na karcie Tylko mój kod można dodać katalogi, które zawierają. *exe* i. pliki *dll* do lokalizacji używanych przez program concurrency visualizer do tylko mój kod.

 Ścieżki. *exe* i. pliki *dll* są przechowywane w pliku śledzenia podczas zbierania śladu.  Zmiana tego ustawienia nie dotyczy żadnych wcześniej zebranych śladów.

## <a name="buffering"></a>Buforowania
 Narzędzie Concurrency Visualizer używa śledzenia zdarzeń systemu Windows (ETW) podczas zbierania śladu.  Funkcja ETW używa różnych buforów, ponieważ przechowuje zdarzenia.  Domyślne ustawienia buforu ETW mogą nie być optymalne we wszystkich przypadkach, a w niektórych przypadkach mogą powodować problemy, takie jak utracone zdarzenia.  Karta buforowanie służy do konfigurowania ustawień buforu funkcji ETW. Aby uzyskać więcej informacji, zobacz [Śledzenie zdarzeń](/windows/win32/etw/event-tracing-portal) i [Struktura EVENT_TRACE_PROPERTIES](/windows/win32/api/evntrace/ns-evntrace-event_trace_properties).

## <a name="filter"></a>filtru
 Na karcie filtr można wybrać zestaw zdarzeń zbieranych przez Wizualizator współbieżności. Wybranie podzestawu zdarzeń ogranicza typy danych, które są wyświetlane w raportach, zmniejsza rozmiar każdego śledzenia i skraca czas wymagany do przetworzenia śladów.

### <a name="clr-events"></a>zdarzenia CLR
 Zdarzenia generowane przez środowisko uruchomieniowe języka wspólnego (CLR) umożliwiają Wizualizatorowi współbieżności rozpoznawanie zarządzanych stosów wywołań.  Jeśli wyłączysz kolekcję zdarzeń CLR, rozmiar śladu zostanie zmniejszony, ale niektóre stosy wywołań nie będą rozpoznawane.  W związku z tym niektóre działania wątków procesora mogą być nieprawidłowo klasyfikowane.

### <a name="collect-for-native-processes"></a>Zbieranie dla procesów natywnych
 Domyślnie zdarzenia CLR są zbierane tylko wtedy, gdy zarządzany proces jest profilowany, ponieważ zwykle nie jest to wymagane w przypadku procesów natywnych.  W niektórych przypadkach (na przykład gdy natywny proces obsługuje środowisko CLR) może być konieczne zebranie zdarzeń CLR dla procesu macierzystego.  W takim przypadku zaznacz pole wyboru **Zbieraj dla procesów natywnych** .

### <a name="disable-rundown-events"></a>Wyłącz zdarzenia uwalniania
 Środowisko CLR generuje zdarzenia od dwóch dostawców: środowisko uruchomieniowe i uwalnianie.  Jeśli chcesz zbierać zdarzenia środowiska uruchomieniowego CLR, ale chcesz uniknąć zbierania zdarzeń uwalniania, zaznacz pole wyboru **Wyłącz zdarzenia uwalniania** .  Zmniejsza to rozmiar pliku śledzenia, który jest generowany przez kolekcję, ale niektóre stosy mogą nie zostać rozpoznane. Aby uzyskać więcej informacji, zobacz [dostawcy CLR ETW](/dotnet/framework/performance/clr-etw-providers).

### <a name="sample-events"></a>Przykładowe zdarzenia
 Za pomocą przykładowych zdarzeń można zbierać stosy wywołań, które są skojarzone z wykonywaniem wątków. Te zdarzenia są zbierane około raz w milisekundach dla wątków, które są wykonywane w bieżącym procesie. Jeśli wyłączysz zbieranie przykładowych zdarzeń, rozmiar zebranych śladów zostanie zmniejszony, ale nie będzie można wyświetlić żadnych stosów wywołań skojarzonych z wykonywaniem wątku.

### <a name="gpu-events"></a>Zdarzenia procesora GPU
 Zdarzenia procesora GPU to zdarzenia generowane przez program DirectX. Jeśli wyłączysz kolekcję zdarzeń procesora GPU, rozmiar zebranego śledzenia zostanie zmniejszony, ale nie będzie można wyświetlić żadnej aktywności procesora GPU w widoku użycie ani działania aparatu DirectX w widoku wątki.

### <a name="file-io-events"></a>Zdarzenia we/wy pliku
 Zdarzenia we/wy pliku reprezentują dostęp do dysku w imieniu bieżącego procesu.  Jeśli wyłączysz zdarzenia we/wy pliku, rozmiar śledzenia zostanie zmniejszony, ale widok wątki nie będzie zgłaszać żadnych informacji na temat kanałów dyskowych ani operacji dyskowych.

## <a name="markers"></a>Wyświetla
 Na karcie **znaczniki** można skonfigurować zestaw dostawców ETW, które są wyświetlane jako znaczniki w wizualizatorze współbieżności.  Można również filtrować kolekcję znaczników na podstawie poziomu ważności i kategorii ETW.  Jeśli używasz [zestawu SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md) i korzystasz z własnego dostawcy znaczników, możesz zarejestrować go w tym miejscu, aby pojawił się w widoku wątki.

### <a name="add-a-new-provider"></a>Dodaj nowego dostawcę
 Jeśli kod używa [zestawu SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md) lub GENERUJE zdarzenia ETW, które są zgodne z konwencją <xref:System.Diagnostics.Tracing.EventSource>, można wyświetlić te zdarzenia w wizualizatorze współbieżności, rejestrując je w tym oknie dialogowym.

 W polu **Nazwa** wprowadź nazwę opisującą typy zdarzeń generowanych przez dostawcę.  W polu **GUID** wprowadź identyfikator GUID, który jest skojarzony z tym dostawcą. (Identyfikator GUID jest skojarzony z każdym dostawcą ETW).

 Opcjonalnie można określić, czy zdarzenia mają być filtrowane z tego dostawcy, na podstawie kategorii lub poziomu ważności.  Możesz użyć pola Kategoria do filtrowania na podstawie kategorii zestawu SDK wizualizatora współbieżności.  W tym celu wprowadź rozdzielany przecinkami ciąg kategorii lub zakresów kategorii.  Określa kategorie zdarzeń w bieżącym dostawcy do wyświetlenia.  W przypadku dodawania dostawcy <xref:System.Diagnostics.Tracing.EventSource> można użyć pola Kategoria do filtrowania według słowa kluczowego ETW.  Ponieważ słowo kluczowe jest wektorem, można użyć rozdzielanego przecinkami ciągu liczb całkowitych, aby określić, które bity w masce są ustawione. Na przykład, "1, 2" ustawia pierwszy i drugi bity, a to jest tłumaczone na 6 w postaci dziesiętnej.

 Za pomocą listy poziomu ważności można odfiltrować zdarzenia, które mają poziom ważności lub ETW, który jest mniejszy niż określona wartość.

### <a name="configure-an-existing-provider"></a>Konfigurowanie istniejącego dostawcy
 Aby edytować ustawienia, które są skojarzone z istniejącym dostawcą, wybierz go z listy, a następnie wybierz przycisk **Edytuj dostawcę** .  Można zmienić nazwę, identyfikator GUID i ustawienia filtrowania.

### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtruj dane znacznika z raportów wizualizatora współbieżności
 Jeśli nie chcesz, aby dane określonego dostawcy były wyświetlane w obszarze śledzenia w przyszłości, usuń zaznaczenie pola wyboru obok dostawcy, który ma zostać usunięty.

## <a name="files"></a>Pliki
 Na karcie **pliki** można określić katalog, w którym pliki śledzenia są przechowywane przy każdym zbieraniu śladu.  Wizualizator współbieżności generuje cztery pliki dla każdego zebranego śledzenia:

- Plik dziennika śledzenia zdarzeń trybu jądra (ETL) (<em>.</em> jądro. etl *)

- Plik dziennika śledzenia zdarzeń trybu użytkownika (<em>.</em> User. etl *)

- Plik danych wizualizatora współbieżności (<em>.</em> CVData*)

- Plik śledzenia Concurrency Visualizer (<em>.</em> CVTrace *)

  Dwa pliki ETL przechowują pierwotne dane śledzenia, a dwa pliki wizualizatora współbieżności przechowują przetwarzane dane.  Nieprzetworzone pliki ETL zazwyczaj nie są używane po przetworzeniu śladu.  Zaznaczenie pola wyboru **Usuń pliki dziennika śledzenia zdarzeń (ETL) po analizie** zmniejsza ilość danych śledzenia przechowywanych na dysku.

## <a name="see-also"></a>Zobacz także
- [Tylko mój kod](../profiling/just-my-code-threads-view.md)
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)