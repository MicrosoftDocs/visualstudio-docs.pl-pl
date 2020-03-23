---
title: Okno dialogowe Ustawienia zaawansowane (wizualizator współbieżności) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911219"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Okno dialogowe Ustawienia zaawansowane (wizualizator współbieżności)
Za pomocą okna dialogowego **Ustawienia zaawansowane** w wizualizatora współbieżności, można kontrolować, jak ślady są zbierane.  Okno dialogowe zawiera karty symboli, Just My Code, buforowanie, filtrowanie, zdarzenia CLR, znaczniki, dostawców i pliki.

## <a name="symbols"></a>Symbole
 Wizualizator współbieżności używa tych samych ustawień symbolu co debuger programu Visual Studio. Wizualizator współbieżności używa ustawień, aby rozwiązać stosy wywołań, które są skojarzone z danymi wydajności.  Podczas przetwarzania śledzenia wizualizator współbieżności uzyskuje dostęp do serwerów symboli, które są określone na stronie ustawień.  Gdy te dane są dostępne za pośrednictwem sieci, przetwarzanie śledzenia spowalnia.  Aby skrócić czas potrzebny do rozpoznawania symboli, można buforować symbole lokalnie. Jeśli symbole zostały pobrane, Visual Studio załaduje je z lokalnej pamięci podręcznej.

## <a name="just-my-code"></a>Tylko mój kod
 Domyślnie just my code to zestaw . *exe* i . *dll* plików, które są skojarzone z bieżącym rozwiązaniem w programie Visual Studio. Wizualizator współbieżności ocenia ten zestaw plików, gdy używasz funkcji Tylko mój kod do filtrowania stosów wywołań. Na karcie Tylko mój kod można dodać katalogi zawierające program . *exe* i . *dll* plików do lokalizacji, które współbieżność wizualizator używa tylko mój kod.

 Ścieżki . *exe* i . pliki *dll* są przechowywane w pliku śledzenia podczas zbierania śledzenia.  Zmiana tego ustawienia nie wpływa na wcześniej zebrane ślady.

## <a name="buffering"></a>Buforowanie
 Wizualizator współbieżności używa śledzenia zdarzeń dla systemu Windows (ETW) podczas zbierania śledzenia.  ETW używa różnych buforów, ponieważ przechowuje zdarzenia.  Domyślne ustawienia buforu ETW może nie być optymalne we wszystkich przypadkach, a w niektórych przypadkach może powodować problemy, takie jak utracone zdarzenia.  Za pomocą karty Buforowanie można skonfigurować ustawienia buforu ETW. Aby uzyskać więcej informacji, zobacz [Śledzenie zdarzeń](/windows/win32/etw/event-tracing-portal) i [EVENT_TRACE_PROPERTIES struktury](/windows/win32/api/evntrace/ns-evntrace-event_trace_properties).

## <a name="filter"></a>Filtr
 Na karcie Filtr można wybrać zestaw zdarzeń, które zbiera wizualizator współbieżności. Wybranie podzbioru zdarzeń ogranicza typy danych, które są wyświetlane w raportach, zmniejsza rozmiar każdego śledzenia i skraca czas wymagany do przetwarzania śladów.

### <a name="clr-events"></a>zdarzenia CLR
 Zdarzenia generowane przez środowisko uruchomieniowe języka wspólnego (CLR) umożliwiają wizualizatorowi współbieżności rozpoznawanie stosów wywołań zarządzanych.  Jeśli wyłączysz kolekcję zdarzeń CLR, rozmiar śledzenia zostanie zmniejszony, ale niektóre stosy wywołań nie rozwiążą.  W rezultacie niektóre działania wątku procesora CPU może być niepoprawnie kategoryzowane.

### <a name="collect-for-native-processes"></a>Zbieraj dla procesów natywnych
 Domyślnie zdarzenia CLR są zbierane tylko wtedy, gdy proces zarządzany jest profilowany, ponieważ są one zwykle niepotrzebne dla procesów natywnych.  W niektórych przypadkach (na przykład, gdy proces macierzysty jest gospodarzem CLR), może być trzeba zebrać zdarzenia CLR dla procesu macierzystego.  W takim przypadku zaznacz pole wyboru **Zbieraj dla procesów natywnych.**

### <a name="disable-rundown-events"></a>Wyłączanie zdarzeń wybiegiem
 Środowisko CLR generuje zdarzenia z dwóch dostawców: runtime i rundown.  Jeśli chcesz zbierać zdarzenia środowiska uruchomieniowego CLR, ale chcesz uniknąć zbierania zdarzeń wybiegiem, zaznacz pole wyboru **Wyłącz zdarzenia uruchamiania.**  Zmniejsza to rozmiar pliku śledzenia, który jest generowany przez kolekcję, ale niektóre stosy mogą nie rozwiązać. Aby uzyskać więcej informacji, zobacz [dostawców CLR ETW](/dotnet/framework/performance/clr-etw-providers).

### <a name="sample-events"></a>Przykładowe zdarzenia
 Można użyć przykładowych zdarzeń do zbierania stosów wywołań, które są skojarzone z wykonywaniem wątku. Te zdarzenia są zbierane około raz na milisekundę dla wątków, które są wykonywane w bieżącym procesie. Jeśli wyłączysz kolekcję zdarzeń przykładowych, rozmiar pobranego śledzenia zostanie zmniejszony, ale nie można wyświetlić żadnych stosów wywołań, które są skojarzone z wykonywaniem wątku.

### <a name="gpu-events"></a>Zdarzenia GPU
 Zdarzenia GPU są zdarzeniami generowanymi przez directx. Jeśli wyłączysz kolekcję zdarzeń GPU, rozmiar zebranego śledzenia zostanie zmniejszony, ale nie można wyświetlić żadnej aktywności gpu w widoku Wykorzystanie lub directx działania aparatu w widoku wątków.

### <a name="file-io-events"></a>Zdarzenia we/wy pliku
 Zdarzenia we/wy pliku reprezentują dostęp do dysku w imieniu bieżącego procesu.  Jeśli wyłączysz zdarzenia we/wy pliku, rozmiar śledzenia zostanie zmniejszony, ale widok wątków nie będzie raportował żadnych informacji o kanałach dysku ani operacjach na dysku.

## <a name="markers"></a>Znaczniki
 Na **markery** kartę, można skonfigurować zestaw dostawców ETW, które są wyświetlane jako znaczniki w wizualizatora współbieżności.  Można również filtrować kolekcji znaczników na podstawie poziomu ważności i kategorii ETW.  Jeśli używasz [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md) i używasz własnego dostawcy znaczników, można zarejestrować go tutaj, tak aby pojawiał się w widoku wątków.

### <a name="add-a-new-provider"></a>Dodawanie nowego dostawcy
 Jeśli kod używa [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md) lub generuje <xref:System.Diagnostics.Tracing.EventSource> zdarzenia ETW, które są zgodne z konwencją, można wyświetlić te zdarzenia w wizualizatorze współbieżności, rejestrując je w tym oknie dialogowym.

 W polu **Nazwa** wprowadź nazwę opisującą typy zdarzeń generowanych przez dostawcę.  W polu **GUID** wprowadź identyfikator GUID skojarzony z tym dostawcą. (Identyfikator GUID jest skojarzony z każdym dostawcą ETW).

 Opcjonalnie można określić, czy odfiltrować zdarzenia z tego dostawcy, na podstawie poziomu kategorii lub ważności.  Za pomocą pola kategorii można filtrować na podstawie kategorii SDK wizualizującego współbieżność.  Aby to zrobić, wprowadź ciąg rozdzielanych przecinkami kategorii lub zakresów kategorii.  Określa kategorie zdarzeń w bieżącym dostawcy, aby pokazać.  Jeśli dodajesz <xref:System.Diagnostics.Tracing.EventSource> dostawcę, możesz użyć pola kategorii do filtrowania według słowa kluczowego ETW.  Ponieważ słowo kluczowe jest maską bitową, można użyć ciągu całkowitych rozdzielanych przecinkami, aby określić, które bity w masce są ustawione. Na przykład "1,2" ustawia pierwszy i drugi bit, a to przekłada się na 6 w przecinku.

 Można użyć listy na poziomie ważności, aby odfiltrować zdarzenia, które mają znaczenie lub poziom ETW, który jest mniejszy niż określona wartość.

### <a name="configure-an-existing-provider"></a>Konfigurowanie istniejącego dostawcy
 Aby edytować ustawienia skojarzone z istniejącym dostawcą, zaznacz go na liście, a następnie wybierz przycisk **Edytuj dostawcę.**  Można zmienić ustawienia nazwy, identyfikatora GUID i filtrowania.

### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtrowanie danych znaczników z raportów wizualizatora współbieżności
 Jeśli nie chcesz, aby dane dla określonego dostawcy były wyświetlane w przyszłych śladach, wyczyść pole wyboru obok dostawcy, którego chcesz usunąć.

## <a name="files"></a>Pliki
 Na karcie **Pliki** można określić katalog, w którym pliki śledzenia są przechowywane za każdym razem, gdy zbierany jest ślad.  Wizualizator współbieżności generuje cztery pliki dla każdego śledzenia zbiera:

- Plik dziennika śledzenia zdarzeń trybu jądra (ETL) (<em>.</em> kernel.etl*)

- Plik dziennika śledzenia zdarzeń w trybie użytkownika (<em>.</em> użytkownik.etl*)

- Plik danych wizualizatora współbieżności (<em>.</em> CVData*)

- Plik śledzenia wizualizatora współbieżności (<em>.</em> CVTrace*)

  Dwa pliki ETL przechowują nieprzetworzone dane śledzenia, a dwa pliki wizualizatora współbieżności przechowują przetworzone dane.  Surowe pliki ETL zazwyczaj nie są używane po przetworzeniu śledzenia.  Zaznaczenie pola wyboru **Usuń pliki dziennika śledzenia zdarzeń (ETL) po analizie** zmniejsza ilość danych śledzenia przechowywanych na dysku.

## <a name="see-also"></a>Zobacz też
- [Tylko mój kod](../profiling/just-my-code-threads-view.md)
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)