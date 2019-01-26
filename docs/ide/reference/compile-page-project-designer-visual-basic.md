---
title: Strona kompilowania, Projektant projektu (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96b56e865c4d8fc190b4f042ae6a0538b9066b9b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008793"
---
# <a name="compile-page-project-designer-visual-basic"></a>Strona kompilowania, Projektant projektu (Visual Basic)

Użyj **skompilować** strony projektanta projektu, aby określić instrukcje kompilacji. Można również określić kompilatora zaawansowane opcje i sprzed kompilacji lub po kompilacji zdarzenia na tej stronie.

Aby uzyskać dostęp do **skompilować** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **skompilować** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Następujące ustawienia pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. W związku z tym **konfiguracji** i **platformy** listy nie są wyświetlane.

 **Konfiguracja**

 Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia są **debugowania** (ustawienie domyślne), **wersji**, lub **wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md) i [jak: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

 **Platforma**

 Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Można określić **dowolny Procesor** (ustawienie domyślne), **x64**, lub **x86**.

## <a name="compiler-configuration-options"></a>Opcje konfiguracji kompilatora

Następujące ustawienia pozwalają włączyć ustawienia kompilatora opcji konfiguracji.

 **Kompiluj ścieżkę wyjściową**

 Określa położenie plików wyjściowych dla tej konfiguracji projektu. W tym polu wpisz ścieżkę dane wyjściowe kompilacji, lub kliknij przycisk **Przeglądaj** przycisk, aby wybrać ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzasz ścieżkę bezwzględną, jego zostanie zapisana jako względna. Domyślna ścieżka to bin\Debug\ lub bin\Release\\.

 Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. **Kompilacji** polecenia **debugowania** menu (F5) umieszcza kompilację w lokalizacji debugowania bez względu na to **ścieżkę wyjściową** określisz. Jednak **kompilacji** polecenia **kompilacji** menu umieszcza go w miejscu określonym przez użytkownika.

 **Opcja explicit** Określa, czy zezwalać na niejawne deklaracji zmiennych. Wybierz **na** będą musieli jawnej deklaracji zmiennych. Powoduje to kompilator, aby włączyć raportowanie błędów, jeśli zmienne nie są deklarowane, zanim zostaną użyte. Wybierz **poza** umożliwia niejawne deklaracji zmiennych.

 To ustawienie odpowiada [/optionexplicit —](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) — opcja kompilatora.

 Jeśli plik kodu źródłowego zawiera [Option Explicit — instrukcja](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), `On` lub `Off` zastępuje wartości w instrukcji **Option Explicit** ustawienie **kompilacji Strona**.

 Podczas tworzenia nowego projektu **Option Explicit** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Explicit** ustawienie w **opcje**  okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Explicit** w **ustawienia domyślne VB** jest **na**.

 Ustawienie **Option Explicit** do `Off` zwykle nie jest dobrym rozwiązaniem. Można błędnego wpisania nazwy zmiennej w przynajmniej jednej lokalizacji, co mogłoby spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.

 **Opcja strict** Określa, czy wymusza semantykę typów ścisłych. Gdy **Option Strict** jest **na**, powodują błąd w czasie kompilacji przez następujące warunki:

-   Niejawne konwersje zawężające

-   Późne powiązania

-   Niejawnego wpisywania, które spowodowało, że `Object` typu

Niejawne błędy konwersji zawężającej wystąpić, gdy jest konwersja typu danych niejawne, który jest konwersją zawężającą. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Konwersje jawne i niejawne](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions), i [rozszerzanie i zwężanie konwersji](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Obiekt jest rozpoznanie późnego wiązania, gdy jest ona przypisana do właściwości lub metody w zmiennej, która jest zadeklarowana jako typ `Object`. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement) i [wczesnego a późne wiązanie](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Niejawne obiektu typu błędy występują, gdy odpowiedni typ nie może być wywnioskowane dla zadeklarowanej zmiennej, więc typ `Object` została wywnioskowana. To przede wszystkim występuje, gdy używasz `Dim` instrukcję, aby zadeklarować zmienną bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer — instrukcja](/dotnet/visual-basic/language-reference/statements/option-infer-statement)i [specyfikacja języka Visual Basic](/dotnet/visual-basic/reference/language-specification).

**Option Strict** ustawienie odpowiada [/optionstrict —](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) — opcja kompilatora.

Jeśli plik kodu źródłowego zawiera [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement), `On` lub `Off` zastępuje wartości w instrukcji **Option Strict** ustawienie **strony kompilacji** .

Podczas tworzenia projektu, **Option Strict** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Strict** ustawienie w **opcje** okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Strict** w **ustawienia domyślne VB** jest **poza**.

**Opcja Strict poszczególne ostrzeżenia.**
**Konfiguracje ostrzeżenie** części **strony kompilacji** ma ustawienia, które odnoszą się do trzech warunków, które powodują błąd kompilacji podczas `Option Strict` znajduje się na. Te ustawienia są następujące:

-   **Niejawna konwersja**

-   **Rozpoznanie późnego wiązania; Wywołanie może się nie powieść w czasie wykonywania**

-   **Niejawne typu; założono, że obiekt**

Po ustawieniu **Option Strict** do **na**, wszystkie trzy ustawienia konfiguracji tych ostrzeżeń są ustawione na **błąd**. Po ustawieniu **Option Strict** do **poza**, wszystkie trzy ustawienia są ustawione na **Brak**.

Można zmienić indywidualnie każdy ostrzeżenie ustawienia konfiguracji **Brak**, **ostrzeżenie**, lub **błąd**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżenia są ustawione na **błąd**, `On` pojawia się w `Option strict` pole. Jeśli wszystkie trzy **Brak**, `Off` pojawia się w tym polu. Dla dowolnej kombinacji tych ustawień **(niestandardowy)** pojawia się.

**Opcja compare** Określa typ porównania ciągów do użycia. Wybierz **binarne** aby poinstruować kompilator, aby używać innych porównań ciągów binarnych, wielkość liter. Wybierz **tekstu** używać porównania ciągów specyficzne dla ustawień regionalnych, bez uwzględniania wielkości liter tekstu.

To ustawienie odpowiada [/optioncompare —](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) — opcja kompilatora.

Jeśli plik kodu źródłowego zawiera [instrukcji porównanie opcji](/dotnet/visual-basic/language-reference/statements/option-compare-statement), `Binary` lub `Text` zastępuje wartości w instrukcji **Option Compare** ustawienie **kompilacji Strona**.

Podczas tworzenia projektu, **Option Compare** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Compare** ustawienie w **opcje** okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Compare** w **ustawienia domyślne VB** jest **binarne**.

**Opcja infer** Określa, czy zezwalać na wnioskowanie o typie lokalnym w deklaracjach zmiennych. Wybierz **na** do Zezwalaj na użycie wnioskowania o typie lokalnym. Wybierz **poza** na wnioskowanie o typie lokalnym bloku.

To ustawienie odpowiada [/optioninfer —](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) — opcja kompilatora.

Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](/dotnet/visual-basic/language-reference/statements/option-infer-statement), `On` lub `Off` zastępuje wartości w instrukcji **Option Infer** ustawienie **strony kompilacji** .

Podczas tworzenia projektu, **Option Infer** ustawienie **strony kompilacji** jest ustawiona na wartość **Option Infer** ustawienie w **opcje**okno dialogowe. Aby wyświetlić lub zmienić ustawienia, w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawienie domyślne początkowej **Option Infer** w **ustawienia domyślne VB** jest **na**.

**Docelowa Procesora** Określa procesor, która ma zostać użyty przez plik wyjściowy. Określ **x86** dla dowolnej 32-bitowy procesor zgodnego z Intel **x64** dla dowolnego 64-bitowy procesor zgodnego z Intel, **ARM** dla dowolnego procesora ARM lub **dowolny Procesor**  do określenia, czy akceptowalny jest każdy procesor. **Dowolny procesor CPU** jest wartością domyślną dla nowych projektów, ponieważ zezwala ona na aplikację do uruchamiania na największą liczbę typów sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**Preferuj 32-bitowe** Jeśli **Preferuj 32 bitowe** pole wyboru jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows. W przeciwnym razie aplikacja działa jako aplikacja 32-bitowego na 32-bitowe wersje systemu Windows i jako aplikacji 64-bitowych w 64-bitowych wersjach systemu Windows.

Uruchamianie zgodnie z aplikacją 64-bitowej podwaja się rozmiar wskaźnika, a może to spowodować problemy ze zgodnością z bibliotek, które są wyłącznie 32-bitowe. Warto uruchomić aplikację jako 64-bitowych, tylko wtedy, gdy działa znacznie szybciej, lub potrzebuje więcej niż 4 GB pamięci.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

-   Na **kompilowania strony**, **Procesora docelowego** listy jest ustawiona na **dowolny Procesor**.

-   Na **strony aplikacji**, **typ aplikacji** lista określa, że projekt jest aplikacją.

-   Na **strony aplikacji**, **platformę docelową** lista określa .NET Framework 4.5.

**Ostrzeżenie konfiguracji** Poniższa tabela zawiera listę warunków kompilacji i odpowiedni poziom powiadomienia **Brak**, **ostrzeżenie**, lub **błąd** dla każdego.

Domyślnie wszystkie ostrzeżenia kompilatora są dodawane do listy zadań podczas kompilacji. Wybierz **Wyłącz wszystkie ostrzeżenia** w celu poinstruowania kompilatora, aby nie problem ostrzeżenia lub błędy. Wybierz **traktowanie wszystkich ostrzeżeń jako błędy** Jeśli chcesz, aby kompilator, aby traktować ostrzeżenia jako błędy, które muszą zostać usunięte.

**Wyłącz wszystkie ostrzeżenia** Określa, czy należy umożliwić kompilatorowi wysyłanie powiadomień, jak to określono w **warunek i powiadomień** tabeli opisane we wcześniejszej części tego dokumentu. Domyślnie to pole wyboru jest wyczyszczone. Zaznacz to pole wyboru, aby poinstruować kompilator, aby nie wystawiać ostrzeżenia lub błędy.

To ustawienie odpowiada [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) — opcja kompilatora.

**Traktuje wszystkie ostrzeżenia jako błędy** Określa, jak ma traktować ostrzeżenia. Domyślnie to pole wyboru jest wyczyszczone, tak aby wszystkie powiadomienia ostrzeżenie pozostały ustawienie **ostrzeżenie**. Zaznacz to pole wyboru, aby zmienić wszystkie powiadomienia ostrzeżenie **błąd**.

Ta opcja jest dostępna tylko wtedy, gdy **Wyłącz wszystkie ostrzeżenia** jest wyczyszczone.

**Generowanie pliku dokumentacji XML** Określa, czy do generowania informacji o dokumentacji. Domyślnie to pole wyboru jest zaznaczone, poinstruowanie kompilatora, aby wygenerować informacje o dokumentacji i uwzględnić go w pliku XML. Wyczyść to pole wyboru, aby poinstruować kompilator, aby pominąć tworzenie dokumentacji.

To ustawienie odpowiada [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) — opcja kompilatora.

**Zarejestruj dla współdziałania COM** Określa, czy Twoją zarządzaną aplikacją udostępni obiektu COM (otokę wywoływaną z modelu COM), który umożliwia obiektu COM na interakcję z aplikacją.

Domyślnie to pole wyboru jest wyczyszczone, która określa, że aplikacja nie zezwala współdziałania z modelem COM. Zaznacz to pole wyboru, aby umożliwić współdziałania z modelem COM.

Ta opcja nie jest dostępne dla projektów Windows aplikacji lub aplikacji Konsolowej.

**Zdarzenia kompilacji** kliknij ten przycisk, aby uzyskać dostęp do **zdarzenia kompilacji** okno dialogowe. To okno dialogowe służy do określania instrukcje dotyczące konfiguracji wstępnej kompilacji i po kompilacji dla projektu. To okno dialogowe dotyczy tylko dla projektów języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie zdarzenia (Visual Basic okno dialogowe)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Zaawansowane opcje kompilacji** kliknij ten przycisk, aby uzyskać dostęp do **ustawienia AdvancedCompiler** okno dialogowe. Użyj **ustawienia AdvancedCompiler** okno dialogowe, aby określić projektu najbardziej zaawansowane właściwości konfiguracji kompilacji. To okno dialogowe dotyczy tylko dla projektów języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Zaawansowane z okno dialogowe Ustawienia kompilatora (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).


## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilator wiersza polecenia programu Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)