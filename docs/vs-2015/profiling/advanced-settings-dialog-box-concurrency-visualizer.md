---
title: Okno dialogowe Ustawienia zaawansowane (Concurrency Visualizer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e1dbe50f3161ca80b4eabe63cbf9264210e9658
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300313"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Okno dialogowe Zaawansowane ustawienia (Concurrency Visualizer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z okna dialogowego **Ustawienia zaawansowane** w wizualizatorze współbieżności, można kontrolować sposób zbierania śladów.  Okno dialogowe zawiera karty symboli, Tylko mój kod, buforowanie, filtrowanie, zdarzenia CLR, znaczniki, dostawcy i pliki.  
  
## <a name="symbols"></a>Symbole  
 Wizualizator współbieżności używa tych samych ustawień symboli co debuger programu Visual Studio. Wizualizator współbieżności używa ustawień do rozwiązywania stosów wywołań skojarzonych z danymi wydajności.  Podczas przetwarzania śladów, Wizualizator współbieżności uzyskuje dostęp do serwerów symboli, które są określone na stronie Ustawienia.  Gdy dostęp do tych danych odbywa się za pośrednictwem sieci, przetwarzanie śledzenia spowalnia się.  Aby skrócić czas wymagany do rozpoznawania symboli, można lokalnie buforować symbole. Jeśli symbole zostały pobrane, program Visual Studio załaduje je z lokalnej pamięci podręcznej.  
  
## <a name="just-my-code"></a>Tylko mój kod  
 Domyślnie Tylko mój kod jest zestawem plików exe i dll, które są skojarzone z bieżącym rozwiązaniem w programie Visual Studio. Wizualizator współbieżności szacuje ten zestaw plików przy użyciu funkcji Tylko mój kod do filtrowania stosów wywołań. Na karcie Tylko mój kod można dodać katalogi zawierające pliki. exe i. dll do lokalizacji, które są używane przez Wizualizator współbieżności dla Tylko mój kod.  
  
 Ścieżki plików exe i dll są przechowywane w pliku śledzenia podczas zbierania śladu.  Zmiana tego ustawienia nie dotyczy żadnych wcześniej zebranych śladów.  
  
## <a name="buffering"></a>Buforowania  
 Narzędzie Concurrency Visualizer używa śledzenia zdarzeń systemu Windows (ETW) podczas zbierania śladu.  Funkcja ETW używa różnych buforów, ponieważ przechowuje zdarzenia.  Domyślne ustawienia buforu ETW mogą nie być optymalne we wszystkich przypadkach, a w niektórych przypadkach mogą powodować problemy, takie jak utracone zdarzenia.  Karta buforowanie służy do konfigurowania ustawień buforu funkcji ETW. Aby uzyskać więcej informacji, zobacz [Śledzenie zdarzeń](https://go.microsoft.com/fwlink/?LinkId=234579) i [Struktura EVENT_TRACE_PROPERTIES](https://go.microsoft.com/fwlink/?LinkId=234580).  
  
## <a name="filter"></a>Filtr  
 Na karcie filtr można wybrać zestaw zdarzeń zbieranych przez Wizualizator współbieżności. Wybranie podzestawu zdarzeń ogranicza typy danych, które są wyświetlane w raportach, zmniejsza rozmiar każdego śledzenia i skraca czas wymagany do przetworzenia śladów.  
  
### <a name="clr-events"></a>Zdarzenia CLR  
 Zdarzenia generowane przez środowisko uruchomieniowe języka wspólnego (CLR) umożliwiają Wizualizatorowi współbieżności rozpoznawanie zarządzanych stosów wywołań.  Jeśli wyłączysz kolekcję zdarzeń CLR, rozmiar śladu zostanie zmniejszony, ale niektóre stosy wywołań nie będą rozpoznawane.  W związku z tym niektóre działania wątków procesora mogą być nieprawidłowo klasyfikowane.  
  
### <a name="collect-for-native-processes"></a>Zbieranie dla procesów natywnych  
 Domyślnie zdarzenia CLR są zbierane tylko wtedy, gdy zarządzany proces jest profilowany, ponieważ zwykle nie jest to wymagane w przypadku procesów natywnych.  W niektórych przypadkach (na przykład gdy natywny proces obsługuje środowisko CLR) może być konieczne zebranie zdarzeń CLR dla procesu macierzystego.  W takim przypadku zaznacz pole wyboru **Zbieraj dla procesów natywnych** .  
  
### <a name="disable-rundown-events"></a>Wyłącz zdarzenia uwalniania  
 Środowisko CLR generuje zdarzenia od dwóch dostawców: środowisko uruchomieniowe i uwalnianie.  Jeśli chcesz zbierać zdarzenia środowiska uruchomieniowego CLR, ale chcesz uniknąć zbierania zdarzeń uwalniania, zaznacz pole wyboru **Wyłącz zdarzenia uwalniania** .  Zmniejsza to rozmiar pliku śledzenia, który jest generowany przez kolekcję, ale niektóre stosy mogą nie zostać rozpoznane. Aby uzyskać więcej informacji, zobacz [dostawcy CLR ETW Providers](https://msdn.microsoft.com/library/0beafad4-b2c8-47f4-b342-83411d57a51f)  
  
### <a name="sample-events"></a>Przykładowe zdarzenia  
 Za pomocą przykładowych zdarzeń można zbierać stosy wywołań, które są skojarzone z wykonywaniem wątków. Te zdarzenia są zbierane około raz w milisekundach dla wątków, które są wykonywane w bieżącym procesie. Jeśli wyłączysz zbieranie przykładowych zdarzeń, rozmiar zebranych śladów zostanie zmniejszony, ale nie będzie można wyświetlić żadnych stosów wywołań skojarzonych z wykonywaniem wątku.  
  
### <a name="gpu-events"></a>Zdarzenia procesora GPU  
 Zdarzenia procesora GPU to zdarzenia generowane przez program DirectX. Jeśli wyłączysz kolekcję zdarzeń procesora GPU, rozmiar zebranego śledzenia zostanie zmniejszony, ale nie będzie można wyświetlić żadnej aktywności procesora GPU w widoku użycie ani działania aparatu DirectX w widoku wątki.  
  
### <a name="file-io-events"></a>Zdarzenia we/wy pliku  
 Zdarzenia we/wy pliku reprezentują dostęp do dysku w imieniu bieżącego procesu.  Jeśli wyłączysz zdarzenia we/wy pliku, rozmiar śledzenia zostanie zmniejszony, ale widok wątki nie będzie zgłaszać żadnych informacji na temat kanałów dyskowych ani operacji dyskowych.  
  
## <a name="markers"></a>Wyświetla  
 Na karcie Znaczniki można skonfigurować zestaw dostawców ETW, które są wyświetlane jako znaczniki w wizualizatorze współbieżności.  Można również filtrować kolekcję znaczników na podstawie poziomu ważności i kategorii ETW.  Jeśli używasz [zestawu SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md) i korzystasz z własnego dostawcy znaczników, możesz zarejestrować go w tym miejscu, aby pojawił się w widoku wątki.  
  
### <a name="adding-a-new-provider"></a>Dodawanie nowego dostawcy  
 Jeśli kod używa [zestawu SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md) lub GENERUJE zdarzenia ETW, które są zgodne z konwencją <xref:System.Diagnostics.Tracing.EventSource>, można wyświetlić te zdarzenia w wizualizatorze współbieżności, rejestrując je w tym oknie dialogowym.  
  
 W polu Nazwa wprowadź nazwę opisującą typy zdarzeń generowanych przez dostawcę.  W polu GUID wprowadź identyfikator GUID, który jest skojarzony z tym dostawcą. (Identyfikator GUID jest skojarzony z każdym dostawcą ETW).  
  
 Opcjonalnie można określić, czy zdarzenia mają być filtrowane z tego dostawcy, na podstawie kategorii lub poziomu ważności.  Możesz użyć pola Kategoria do filtrowania na podstawie kategorii zestawu SDK wizualizatora współbieżności.  W tym celu wprowadź rozdzielany przecinkami ciąg kategorii lub zakresów kategorii.  Określa kategorie zdarzeń w bieżącym dostawcy do wyświetlenia.  W przypadku dodawania dostawcy <xref:System.Diagnostics.Tracing.EventSource> można użyć pola Kategoria do filtrowania według słowa kluczowego ETW.  Ponieważ słowo kluczowe jest wektorem, można użyć rozdzielanego przecinkami ciągu liczb całkowitych, aby określić, które bity w masce są ustawione. Na przykład, "1, 2" ustawia pierwszy i drugi bity, a to jest tłumaczone na 6 w postaci dziesiętnej.  
  
 Za pomocą listy poziomu ważności można odfiltrować zdarzenia, które mają poziom ważności lub ETW, który jest mniejszy niż określona wartość.  
  
### <a name="configuring-an-existing-provider"></a>Konfigurowanie istniejącego dostawcy  
 Aby edytować ustawienia, które są skojarzone z istniejącym dostawcą, wybierz go z listy, a następnie wybierz przycisk **Edytuj dostawcę** .  Można zmienić nazwę, identyfikator GUID i ustawienia filtrowania.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtruj dane znacznika z raportów wizualizatora współbieżności  
 Jeśli nie chcesz, aby dane określonego dostawcy były wyświetlane w obszarze śledzenia w przyszłości, usuń zaznaczenie pola wyboru obok dostawcy, który ma zostać usunięty.  
  
## <a name="files"></a>Pliki  
 Na karcie **pliki** można określić katalog, w którym pliki śledzenia są przechowywane przy każdym zbieraniu śladu.  Wizualizator współbieżności generuje cztery pliki dla każdego zebranego śledzenia:  
  
- Plik dziennika śledzenia zdarzeń trybu jądra (ETL) (*. kernel. etl)  
  
- Plik dziennika śledzenia zdarzeń trybu użytkownika (*. User. etl)  
  
- Plik danych wizualizatora współbieżności (*. CVData)  
  
- Plik śledzenia Concurrency Visualizer (*. CVTrace  
  
  Dwa pliki ETL przechowują pierwotne dane śledzenia, a dwa pliki wizualizatora współbieżności przechowują przetwarzane dane.  Nieprzetworzone pliki ETL zazwyczaj nie są używane po przetworzeniu śladu.  Zaznaczenie pola wyboru **Usuń pliki dziennika śledzenia zdarzeń (ETL) po analizie** zmniejsza ilość danych śledzenia przechowywanych na dysku.  
  
## <a name="see-also"></a>Zobacz też  
 [Tylko mój kod](../profiling/just-my-code-threads-view.md)   
 [Znaczniki Concurrency Visualizer](../profiling/concurrency-visualizer-markers.md)
