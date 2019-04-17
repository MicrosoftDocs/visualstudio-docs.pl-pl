---
title: Strona kompilowania, Projektant (Visual Basic) projektu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 65
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3dd58013cb26e8533a5b898a0e5cd1df3be1b262
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649059"
---
# <a name="compile-page-project-designer-visual-basic"></a>Strona kompilowania, Projektant projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj **skompilować** strony projektanta projektu, aby określić instrukcje kompilacji. Można również określić kompilatora zaawansowane opcje i sprzed kompilacji lub po kompilacji zdarzenia na tej stronie.  
  
 Aby uzyskać dostęp do **skompilować** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **skompilować** kartę.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Konfiguracja i platforma  
 Następujące ustawienia pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.  
  
> [!NOTE]
>  Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. W związku z tym **konfiguracji** i **platformy** listy nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Konfiguracja**  
 Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia są **debugowania** (ustawienie domyślne), **wersji**, lub **wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) i [jak: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Platforma**  
 Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Można określić **dowolny Procesor** (ustawienie domyślne), **x64**, lub **x86**. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="compiler-configuration-options"></a>Opcje konfiguracji kompilatora  
 Następujące ustawienia pozwalają włączyć ustawienia kompilatora opcji konfiguracji.  
  
 **Kompiluj ścieżkę wyjściową**  
 Określa położenie plików wyjściowych dla tej konfiguracji projektu. W tym polu wpisz ścieżkę dane wyjściowe kompilacji, lub kliknij przycisk **Przeglądaj** przycisk, aby wybrać ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzasz ścieżkę bezwzględną, jego zostanie zapisana jako względna. Domyślna ścieżka to bin\Debug\ lub bin\Release\\. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. **Kompilacji** polecenia **debugowania** menu (F5) umieszcza kompilację w lokalizacji debugowania bez względu na to **ścieżkę wyjściową** określisz. Jednak **kompilacji** polecenia **kompilacji** menu umieszcza go w miejscu określonym przez użytkownika. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Opcja explicit**  
 Określa, czy zezwalać na niejawne deklaracji zmiennych. Wybierz **na** będą musieli jawnej deklaracji zmiennych. Powoduje to kompilator, aby włączyć raportowanie błędów, jeśli zmienne nie są deklarowane, zanim zostaną użyte. Wybierz **poza** umożliwia niejawne deklaracji zmiennych.  
  
 To ustawienie odpowiada [/optionexplicit —](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) — opcja kompilatora.  
  
 Jeśli plik kodu źródłowego zawiera [Option Explicit — instrukcja](http://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), `On` lub `Off` zastępuje wartości w instrukcji **Option Explicit** ustawienie **kompilacji Strona**.  
  
 Podczas tworzenia nowego projektu **Option Explicit** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Explicit** ustawienie w **opcje**  okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Explicit** w **ustawienia domyślne VB** jest **na**.  
  
 Ustawienie **Option Explicit** do `Off` zwykle nie jest dobrym rozwiązaniem. Można błędnego wpisania nazwy zmiennej w przynajmniej jednej lokalizacji, co mogłoby spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.  
  
 **Opcja strict**  
 Określa, czy wymusza semantykę typów ścisłych. Gdy **Option Strict** jest **na**, powodują błąd w czasie kompilacji przez następujące warunki:  
  
- Niejawne konwersje zawężające  
  
- Późne powiązania  
  
- Niejawnego wpisywania, które spowodowało, że `Object` typu  
  
  Niejawne błędy konwersji zawężającej wystąpić, gdy jest konwersja typu danych niejawne, który jest konwersją zawężającą. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Konwersje jawne i niejawne](http://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66), i [rozszerzanie i zwężanie konwersji](http://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).  
  
  Obiekt jest rozpoznanie późnego wiązania, gdy jest ona przypisana do właściwości lub metody w zmiennej, która jest zadeklarowana jako typ `Object`. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) i [wczesnego a późne wiązanie](http://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).  
  
  Niejawne obiektu typu błędy występują, gdy odpowiedni typ nie może być wywnioskowane dla zadeklarowanej zmiennej, więc typ `Object` została wywnioskowana. To przede wszystkim występuje, gdy używasz `Dim` instrukcję, aby zadeklarować zmienną bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Infer — instrukcja](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)i [specyfikacja języka Visual Basic](http://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).  
  
  **Option Strict** ustawienie odpowiada [/optionstrict —](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) — opcja kompilatora.  
  
  Jeśli plik kodu źródłowego zawiera [Option Strict — instrukcja](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), `On` lub `Off` zastępuje wartości w instrukcji **Option Strict** ustawienie **strony kompilacji** .  
  
  Podczas tworzenia projektu, **Option Strict** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Strict** ustawienie w **opcje** okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Strict** w **ustawienia domyślne VB** jest **poza**.  
  
  **Opcja Strict poszczególne ostrzeżenia.** **Konfiguracje ostrzeżenie** części **strony kompilacji** ma ustawienia, które odnoszą się do trzech warunków, które powodują błąd kompilacji podczas `Option Strict` znajduje się na. Te ustawienia są następujące:  
  
- **Niejawna konwersja**  
  
- **Rozpoznanie późnego wiązania; Wywołanie może się nie powieść w czasie wykonywania**  
  
- **Niejawne typu; założono, że obiekt**  
  
  Po ustawieniu **Option Strict** do **na**, wszystkie trzy ustawienia konfiguracji tych ostrzeżeń są ustawione na **błąd**. Po ustawieniu **Option Strict** do **poza**, wszystkie trzy ustawienia są ustawione na **Brak**.  
  
  Można zmienić indywidualnie każdy ostrzeżenie ustawienia konfiguracji **Brak**, **ostrzeżenie**, lub **błąd**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżenia są ustawione na **błąd**, `On` pojawia się w `Option strict` pole. Jeśli wszystkie trzy **Brak**, `Off` pojawia się w tym polu. Dla dowolnej kombinacji tych ustawień **(niestandardowy)** pojawia się.  
  
  **Opcja compare**  
  Określa typ porównania ciągów do użycia. Wybierz **binarne** aby poinstruować kompilator, aby używać innych porównań ciągów binarnych, wielkość liter. Wybierz **tekstu** używać porównania ciągów specyficzne dla ustawień regionalnych, bez uwzględniania wielkości liter tekstu.  
  
  To ustawienie odpowiada [/optioncompare —](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) — opcja kompilatora.  
  
  Jeśli plik kodu źródłowego zawiera [instrukcji porównanie opcji](http://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), `Binary` lub `Text` zastępuje wartości w instrukcji **Option Compare** ustawienie **kompilacji Strona**.  
  
  Podczas tworzenia projektu, **Option Compare** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Compare** ustawienie w **opcje** okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Compare** w **ustawienia domyślne VB** jest **binarne**.  
  
  **Opcja infer**  
  Określa, czy zezwalać na wnioskowanie o typie lokalnym w deklaracjach zmiennych. Wybierz **na** do Zezwalaj na użycie wnioskowania o typie lokalnym. Wybierz **poza** na wnioskowanie o typie lokalnym bloku.  
  
  To ustawienie odpowiada [/optioninfer —](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) — opcja kompilatora.  
  
  Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), `On` lub `Off` zastępuje wartości w instrukcji **Option Infer** ustawienie **strony kompilacji** .  
  
  Podczas tworzenia projektu, **Option Infer** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Infer** ustawienie w **opcje**okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Infer** w **ustawienia domyślne VB** jest **na**.  
  
  **Docelowy adres CPU**  
  Określa procesor, która ma zostać użyty przez plik wyjściowy. Określ **x86** dla dowolnej 32-bitowy procesor zgodnego z Intel **x64** dla dowolnego 64-bitowy procesor zgodnego z Intel, **ARM** dla dowolnego procesora ARM lub **dowolny Procesor**  do określenia, czy akceptowalny jest każdy procesor. **Dowolny procesor CPU** jest wartością domyślną dla nowych projektów, ponieważ zezwala ona na aplikację do uruchamiania na największą liczbę typów sprzętu.  
  
  Aby uzyskać więcej informacji, zobacz [/platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
  **Preferuj 32-bitowe**  
  Jeśli **Preferuj 32 bitowe** pole wyboru jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows. W przeciwnym razie aplikacja działa jako aplikacja 32-bitowego na 32-bitowe wersje systemu Windows i jako aplikacji 64-bitowych w 64-bitowych wersjach systemu Windows.  
  
  Uruchamianie zgodnie z aplikacją 64-bitowej podwaja się rozmiar wskaźnika, a może to spowodować problemy ze zgodnością z bibliotek, które są wyłącznie 32-bitowe. Warto uruchomić aplikację jako 64-bitowych, tylko wtedy, gdy działa znacznie szybciej, lub potrzebuje więcej niż 4 GB pamięci.  
  
  To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:  
  
- Na **kompilowania strony**, **Procesora docelowego** listy jest ustawiona na **dowolny Procesor**.  
  
- Na **strony aplikacji**, **typ aplikacji** lista określa, że projekt jest aplikacją.  
  
- Na **strony aplikacji**, **platformę docelową** lista określa .NET Framework 4.5.  
  
  **Ostrzeżenie konfiguracji**  
  Poniższa tabela zawiera listę warunków kompilacji i odpowiedni poziom powiadomienia **Brak**, **ostrzeżenie**, lub **błąd** dla każdego.  
  
  Domyślnie wszystkie ostrzeżenia kompilatora są dodawane do listy zadań podczas kompilacji. Wybierz **Wyłącz wszystkie ostrzeżenia** w celu poinstruowania kompilatora, aby nie problem ostrzeżenia lub błędy. Wybierz **traktowanie wszystkich ostrzeżeń jako błędy** Jeśli chcesz, aby kompilator, aby traktować ostrzeżenia jako błędy, które muszą zostać usunięte.  
  
  **Wyłącz wszystkie ostrzeżenia**  
  Określa, czy należy umożliwić kompilatorowi wysyłanie powiadomień, jak to określono w **warunek i powiadomień** tabeli opisane we wcześniejszej części tego dokumentu. Domyślnie to pole wyboru jest wyczyszczone. Zaznacz to pole wyboru, aby poinstruować kompilator, aby nie wystawiać ostrzeżenia lub błędy.  
  
  To ustawienie odpowiada [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) — opcja kompilatora.  
  
  **Traktuje wszystkie ostrzeżenia jako błędy**  
  Określa, jak ma traktować ostrzeżenia. Domyślnie to pole wyboru jest wyczyszczone, tak aby wszystkie powiadomienia ostrzeżenie pozostały ustawienie **ostrzeżenie**. Zaznacz to pole wyboru, aby zmienić wszystkie powiadomienia ostrzeżenie **błąd**.  
  
  Ta opcja jest dostępna tylko wtedy, gdy **Wyłącz wszystkie ostrzeżenia** jest wyczyszczone.  
  
  **Generowanie pliku dokumentacji XML**  
  Określa, czy do generowania informacji o dokumentacji. Domyślnie to pole wyboru jest zaznaczone, poinstruowanie kompilatora, aby wygenerować informacje o dokumentacji i uwzględnić go w pliku XML. Wyczyść to pole wyboru, aby poinstruować kompilator, aby pominąć tworzenie dokumentacji.  
  
  To ustawienie odpowiada [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) — opcja kompilatora.  
  
  **Zarejestruj dla współdziałania z modelem COM**  
  Określa, czy Twoją zarządzaną aplikacją udostępni obiektu COM (otokę wywoływaną z modelu COM), który umożliwia obiektu COM na interakcję z aplikacją.  
  
  Domyślnie to pole wyboru jest wyczyszczone, która określa, że aplikacja nie zezwala współdziałania z modelem COM. Zaznacz to pole wyboru, aby umożliwić współdziałania z modelem COM.  
  
  Ta opcja nie jest dostępne dla projektów Windows aplikacji lub aplikacji Konsolowej.  
  
  **Zdarzenia kompilacji**  
  Kliknij ten przycisk, aby uzyskać dostęp do **zdarzenia kompilacji** okno dialogowe. To okno dialogowe służy do określania instrukcje dotyczące konfiguracji wstępnej kompilacji i po kompilacji dla projektu. To okno dialogowe dotyczy tylko dla projektów języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie zdarzenia (Visual Basic okno dialogowe)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
  **Zaawansowane opcje kompilacji**  
  Kliknij ten przycisk, aby uzyskać dostęp do **ustawienia AdvancedCompiler** okno dialogowe. Użyj **ustawienia AdvancedCompiler** okno dialogowe, aby określić projektu najbardziej zaawansowane właściwości konfiguracji kompilacji. To okno dialogowe dotyczy tylko dla projektów języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Zaawansowane z okno dialogowe Ustawienia kompilatora (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)   
 [Zarządzanie właściwościami kompilacja](http://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Kompilator wiersza polecenia programu Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
