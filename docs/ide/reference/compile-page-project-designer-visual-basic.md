---
title: Strona kompilowania, Projektant projektu (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7a97068b70a76dfe343de5fa68db77d2ce9781
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111309"
---
# <a name="compile-page-project-designer-visual-basic"></a>Strona kompilowania, Projektant projektu (Visual Basic)

Użyj **strony Kompilacja** projektanta projektu, aby określić instrukcje kompilacji. Można również określić opcje zaawansowanego kompilatora i zdarzenia przed kompilacją lub po kompilacji na tej stronie.

Aby uzyskać dostęp do strony **Kompilacja,** wybierz węzeł projektu (a nie węzeł **Rozwiązanie)** w **Eksploratorze rozwiązań**. Następnie wybierz polecenie **Projekt**, **Właściwości** na pasku menu. Po wyświetleniu projektanta projektu kliknij kartę **Kompilacja.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe ustawienia umożliwiają wybranie konfiguracji i platformy do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W uproszczonych konfiguracjach kompilacji system projektu określa, czy chcesz utworzyć wersję debugowania lub wersji. W związku z tym **konfiguracja** i **platformy** listy nie są wyświetlane.

**Konfiguracja**

Określa ustawienia konfiguracji, które mają być wyświetlane lub modyfikowane. Ustawienia to **Debug** (domyślnie), **Zwolnij**lub **Wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md) i [jak: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

**Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Można określić **dowolny procesor** (domyślny), **x64**lub **x86**.

## <a name="compiler-configuration-options"></a>Opcje konfiguracji kompilatora

Poniższe ustawienia umożliwiają ustawienie opcji konfiguracji kompilatora.

**Tworzenie ścieżki wyjściowej**

Określa lokalizację plików wyjściowych dla konfiguracji tego projektu. Wpisz ścieżkę danych wyjściowych kompilacji w tym polu lub kliknij przycisk **Przeglądaj,** aby wybrać ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, zostanie on zapisany jako względny. Domyślną ścieżką jest bin\Debug\\\lub bin\Release .

W uproszczonych konfiguracjach kompilacji system projektu określa, czy chcesz utworzyć wersję debugowania lub wersji. Polecenie **Kompilacja** z menu **Debugowanie** (F5) umieści kompilację w lokalizacji debugowania, niezależnie od określonej **ścieżki wyjściowej.** Jednak **build** polecenia z **build** menu umieszcza go w lokalizacji, którą określisz.

**Opcja jawna**

Określa, czy zezwolić na niejawną deklarację zmiennych. Wybierz **włącz,** aby wymagać jawnej deklaracji zmiennych. Powoduje to, że kompilator do raportowania błędów, jeśli zmienne nie są zadeklarowane przed ich użyciem. Wybierz **opcję Wyłączone,** aby zezwolić na niejawną deklarację zmiennych.

To ustawienie odpowiada opcji kompilatora [/optionexplicit.](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)

Jeśli plik kodu źródłowego zawiera oświadczenie `On` `Off` [option explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)statement, lub wartość w instrukcji zastępuje ustawienie **Jawne opcji** na stronie **Kompilacja**.

Podczas tworzenia nowego projektu ustawienie **Jawne opcje** na **stronie Kompilacja** jest ustawione na wartość ustawienia **Jawne opcje** w oknie dialogowym **Opcje.** Aby wyświetlić lub zmienić ustawienie w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **Projekty i rozwiązania**, a następnie kliknij pozycję **Domyślne ustawienia VB**. Początkowe ustawienie domyślne **opcji Jawne** w **ustawieniach domyślnych VB** to **Wł.**

Opcja **ustawiania Jawne** dla `Off` zazwyczaj nie jest dobrą praktyką. Można błędnie nazwa zmiennej w jednej lub kilku lokalizacjach, co może spowodować nieoczekiwane wyniki po uruchomieniu programu.

**Opcja ścisła**

Określa, czy semantyka typu ścisłego ma być wymuszana. Gdy **opcja Strict** jest **wł.,** następujące warunki powodują błąd w czasie kompilacji:

- Niejawne konwersje zawężające

- Późne wiązanie

- Niejawne wpisywanie, które powoduje `Object` typ

Niejawne błędy konwersji zawężenia występują, gdy istnieje niejawna konwersja typu danych, która jest konwersją zawężającą. Aby uzyskać więcej informacji, zobacz [Opcja Ścisłe oświadczenie](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Konwersje niejawne i jawne](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)oraz [Konwersje rozszerzające i zawężające](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Obiekt jest późno związany, gdy jest przypisany do właściwości lub metody zmiennej, która jest zadeklarowana jako typu `Object`. Aby uzyskać więcej informacji, zobacz [Opcja Ścisłe oświadczenie](/dotnet/visual-basic/language-reference/statements/option-strict-statement) oraz [Wczesne i Późne powiązanie](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Błędy typu obiektu niejawnego występują, gdy nie można wywnioskować odpowiedniego typu dla zadeklarowanej zmiennej, `Object` więc typ jest wywnioskowany. Dzieje się tak przede `Dim` wszystkim, gdy używasz `As` instrukcji do `Option Infer` deklarowania zmiennej bez użycia klauzuli i jest wyłączona. Aby uzyskać więcej informacji, zobacz [Instrukcja ścisła opcji,](/dotnet/visual-basic/language-reference/statements/option-strict-statement) [Instrukcja wywnioskowania opcji](/dotnet/visual-basic/language-reference/statements/option-infer-statement)i [Specyfikacja języka Visual Basic](/dotnet/visual-basic/reference/language-specification).

Ustawienie **Ścisłe opcje** odpowiada opcji kompilatora [/optionstrict.](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)

Jeśli plik kodu źródłowego zawiera [instrukcję Option Strict Statement,](/dotnet/visual-basic/language-reference/statements/option-strict-statement) `On` lub `Off` wartość w instrukcji zastępuje ustawienie **Option Strict** na stronie **Kompilacja**.

Podczas tworzenia projektu ustawienie **Ścisłe opcje** na **stronie Kompilacja** jest ustawione na wartość ustawienia **Option Strict** w oknie dialogowym **Opcje.** Aby wyświetlić lub zmienić ustawienie w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **Projekty i rozwiązania**, a następnie kliknij pozycję **Domyślne ustawienia VB**. Początkowe ustawienie domyślne **opcji Ścisłe** w **ustawieniach domyślnych VB** jest **wyłączone**.

**Opcja Ścisłe ostrzeżenia indywidualne**

**Ostrzeżenie konfiguracje** sekcji **compile strony** ma ustawienia, które odpowiadają trzy warunki, które `Option Strict` powodują błąd w czasie kompilacji, gdy jest włączony. Poniżej przedstawiono następujące ustawienia:

- **Konwersja niejawna**

- **Późne wiązanie; połączenie może zakończyć się niepowodzeniem w czasie wykonywania**

- **Typ niejawny; zakładany obiekt**

Po ustawieniu **opcji Ścisła** **na Wł.,** wszystkie trzy z tych ustawień konfiguracji ostrzeżenia są ustawione na **Błąd**. Po ustawieniu **opcji Ścisła** na **Wyłączona**wszystkie trzy ustawienia są ustawione na **Brak**.

Można indywidualnie zmienić każde ustawienie konfiguracji ostrzeżenia na **Brak,** **Ostrzeżenie**lub **Błąd**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżenia `On` są `Option strict` ustawione na **Błąd,** pojawi się w polu. Jeśli wszystkie trzy są `Off` ustawione na **Brak,** pojawi się w tym polu. Dla dowolnej innej kombinacji tych ustawień pojawia się **(niestandardowe).**

**Porównanie opcji**

Określa typ porównania ciągów do użycia. Wybierz **opcję Binarny,** aby poinstruować kompilatora, aby używał binarnych porównań ciągów z uwzględnieniem wielkości liter. Wybierz **opcję Tekst,** aby użyć porównań ciągów tekstowych specyficznych dla ustawień regionalnych, niewrażliwych na rozmiary.

To ustawienie odpowiada opcji kompilatora [/optioncompare.](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)

Jeśli plik kodu źródłowego zawiera [instrukcję porównywania opcji,](/dotnet/visual-basic/language-reference/statements/option-compare-statement) `Binary` lub `Text` wartość w instrukcji zastępuje ustawienie **Porównanie opcji** na stronie **Kompilacja**.

Podczas tworzenia projektu ustawienie **Porównanie opcji** na stronie **Kompilacja** jest ustawione na wartość ustawienia Porównanie **opcji** w oknie dialogowym **Opcje.** Aby wyświetlić lub zmienić ustawienie w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **Projekty i rozwiązania**, a następnie kliknij pozycję **Domyślne ustawienia VB**. Początkowe ustawienie domyślne **opcji Porównaj** w **ustawieniach domyślnych VB** to **Binary**.

**Wywnioskować opcję**

Określa, czy w deklaracjach zmiennych zezwolić na wnioskowanie o typie lokalnym. Wybierz **włącz,** aby zezwolić na użycie wnioskowania o typie lokalnym. Wybierz **opcję Wyłączone,** aby zablokować wnioskowanie o typie lokalnym.

To ustawienie odpowiada opcji kompilatora [/optioninfer.](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)

Jeśli plik kodu źródłowego zawiera [instrukcję wnioskowania opcji,](/dotnet/visual-basic/language-reference/statements/option-infer-statement) `On` lub `Off` wartość w instrukcji zastępuje ustawienie **Wnioskowanie opcji** na stronie **Kompilacja**.

Podczas tworzenia projektu ustawienie **Wnioskowanie opcji** na **stronie Kompilacja** jest ustawione na wartość ustawienia **Wywnioskować opcji** w oknie dialogowym **Opcje.** Aby wyświetlić lub zmienić ustawienie w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **Projekty i rozwiązania**, a następnie kliknij pozycję **Domyślne ustawienia VB**. Początkowe ustawienie domyślne **opcji Wywnioskowanie** w **ustawieniach domyślnych VB** to **Wł.**

**Docelowy procesor**

Określa procesor, na który ma docelow plik wyjściowy. Określ **x86** dla dowolnego 32-bitowego procesora zgodnego z procesorem Intel, **x64** dla dowolnego 64-bitowego procesora zgodnego z procesorem Intel, **ARM** dla dowolnego procesora ARM lub **dowolnego procesora,** aby określić, że dowolny procesor jest dopuszczalny. **Każdy procesor CPU** jest wartością domyślną dla nowych projektów, ponieważ umożliwia aplikacji uruchamianie na największej liczbie typów sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**Preferuj 32-bitowe**

Jeśli zaznaczone jest pole wyboru **Preferuj32-bitowe,** aplikacja działa jako aplikacja 32-bitowa zarówno w 32-bitowych, jak i 64-bitowych wersjach systemu Windows. W przeciwnym razie aplikacja działa jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bitowa w 64-bitowych wersjach systemu Windows.

Uruchamianie jako aplikacja 64-bitowa podwaja rozmiar wskaźnika i może powodować problemy ze zgodnością z bibliotekami, które są wyłącznie 32-bitowe. Warto uruchomić aplikację jako 64-bitową tylko wtedy, gdy działa znacznie szybciej lub potrzebuje więcej niż 4 GB pamięci.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na **stronie Kompilacja**lista **docelowego procesora** jest **ustawiona**na Dowolny procesor .

- Na **stronie aplikacji**lista **Typ aplikacji** określa, że projekt jest aplikacją.

- Na **stronie aplikacji**lista **docelowa framework** określa .NET Framework 4.5.

**Konfiguracje ostrzegawcze**

W tej tabeli wymieniono warunki kompilacji i odpowiedni poziom powiadomień **brak,** **ostrzeżenie**lub **błąd** dla każdego z nich.

Domyślnie wszystkie ostrzeżenia kompilatora są dodawane do listy zadań podczas kompilacji. Wybierz **opcję Wyłącz wszystkie ostrzeżenia,** aby poinstruować kompilatora, aby nie wystawiał ostrzeżeń ani błędów. Wybierz **opcję Traktuj wszystkie ostrzeżenia jako błędy,** jeśli chcesz, aby kompilator traktował ostrzeżenia jako błędy, które muszą zostać naprawione.

**Wyłącz wszystkie ostrzeżenia**

Określa, czy kompilator ma zezwalać kompilatorowi na wystawianie powiadomień zgodnie z tabelą **Warunek i powiadomienie** opisaną wcześniej w tym dokumencie. To pole wyboru jest domyślnie wyczyszczone. Zaznacz to pole wyboru, aby poinstruować kompilatora, aby nie wystawiał ostrzeżeń ani błędów.

To ustawienie odpowiada opcji kompilatora [/nowarn.](/dotnet/visual-basic/reference/command-line-compiler/nowarn)

**Traktuj wszystkie ostrzeżenia jako błędy**

Określa sposób leczenia ostrzeżeń. Domyślnie to pole wyboru jest wyczyszczone, dzięki czemu wszystkie powiadomienia ostrzegawcze pozostają ustawione na **Ostrzeżenie**. Zaznacz to pole wyboru, aby zmienić wszystkie powiadomienia ostrzegawcze na **Błąd**.

Ta opcja jest dostępna tylko **wtedy, gdy wyłącz wszystkie ostrzeżenia** są wyczyszczone.

**Generowanie pliku dokumentacji XML**

Określa, czy mają być generowane informacje o dokumentacji. Domyślnie to pole wyboru jest zaznaczone, instruując kompilator do generowania informacji o dokumentacji i dołączania ich do pliku XML. Wyczyść to pole wyboru, aby poinstruować kompilatora, aby nie tworzył dokumentacji.

To ustawienie odpowiada opcji kompilatora [/doc.](/dotnet/visual-basic/reference/command-line-compiler/doc)

**Zarejestruj się w com interop**

Określa, czy aplikacja zarządzana będzie uwidaczniać obiekt COM (otokę wywoływaną przez COM), która umożliwia obiektowi COM interakcję z aplikacją.

Domyślnie to pole wyboru jest wyczyszczone, co określa, że aplikacja nie zezwala na współdziałania COM. Zaznacz to pole wyboru, aby zezwolić na połączenie com.

Ta opcja nie jest dostępna w przypadku projektów aplikacji systemu Windows lub aplikacji konsoli.

**Tworzenie zdarzeń**

Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **Zdarzenia kompilacji.** To okno dialogowe służy do określania instrukcji konfiguracji pre-build i po kompilacji dla projektu. To okno dialogowe dotyczy tylko projektów języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Okno dialogowe Tworzenie zdarzeń (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Zaawansowane opcje kompilacji**

Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **AdvancedCompiler Settings.** Okno dialogowe **Zaawansowane ustawienia kompilatora** służy do określania właściwości zaawansowanej konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko projektów języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Okno dialogowe Zaawansowane ustawienia kompilatora (Visual Basic).](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

## <a name="see-also"></a>Zobacz też

- [Porady: określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic Kompilator wiersza polecenia](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Porady: tworzenie i edycja konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
