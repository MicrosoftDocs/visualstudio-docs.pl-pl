---
title: Strona kompilowania, Projektant projektu (Visual Basic) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db830e04388b7465c941e2fdf069b49f98951a1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660824"
---
# <a name="compile-page-project-designer-visual-basic"></a>Strona kompilowania, Projektant projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj strony **kompilacja** projektanta projektu, aby określić instrukcje kompilacji. Na tej stronie można także określić zaawansowane opcje kompilatora oraz zdarzenia przed kompilacją lub po kompilacji.

 Aby uzyskać dostęp do strony **kompilowania** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **projekt**, **Właściwości** na pasku menu. Gdy pojawi się Projektant projektu, kliknij kartę **kompilacja** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma
 Poniższe ustawienia umożliwiają wybranie konfiguracji i platformy do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. W związku z tym listy **konfiguracji** i **platformy** nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Konfiguracja** Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia są **debugowane** (ustawienie domyślne), **wydanie**lub **wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) oraz [instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

 **Platforma** Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Można określić **dowolny procesor** (wartość domyślna), **x64**lub **x86**. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="compiler-configuration-options"></a>Opcje konfiguracji kompilatora
 Poniższe ustawienia umożliwiają ustawienie opcji konfiguracji kompilatora.

 **Ścieżka wyjściowa kompilacji** Określa lokalizację plików wyjściowych dla konfiguracji projektu. W tym polu wpisz ścieżkę do danych wyjściowych kompilacji lub kliknij przycisk **Przeglądaj** , aby wybrać ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, zostanie ona zapisana jako względna. Ścieżka domyślna to bin\Debug\ lub bin\Release \\ . Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. Polecenie **Build** z menu **Debuguj** (F5) umieści kompilację w lokalizacji debugowania niezależnie od określonej **ścieżki wyjściowej** . Jednak polecenie **Build** z menu **kompilacja** umieszcza je w określonej lokalizacji. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Opcja Explicit** Określa, czy zezwalać na niejawną deklarację zmiennych. Wybierz opcję **Włącz** , aby wymagać jawnej deklaracji zmiennych. Powoduje to, że kompilator zgłasza błędy, jeśli zmienne nie są zadeklarowane przed użyciem. Wybierz pozycję **wyłączone** , aby zezwolić na niejawną deklarację zmiennych.

 To ustawienie odpowiada opcji kompilatora [/optionexplicit —](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) .

 Jeśli plik kodu źródłowego zawiera [instrukcję Option Explicit](https://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), `On` `Off` wartość lub w instrukcji przesłania ustawienie **opcji jawnej** na **stronie kompilowania**.

 Podczas tworzenia nowego projektu **opcja ustawienie jawne** na **stronie kompilowania** jest ustawiana na wartość ustawienie **opcji jawne** w oknie dialogowym **Opcje** . Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie **opcji Explicit** w **ustawieniach domyślnych języka vb** jest **włączone**.

 Ustawienie **opcji Explicit** `Off` to generalnie nie jest dobrym rozwiązaniem. W co najmniej jednej lokalizacji można wypróbować nazwę zmiennej, co spowodowałoby nieoczekiwane wyniki, gdy program zostanie uruchomiony.

 **Option Strict** Określa, czy należy wymusić semantykę typu Strict. Gdy **opcja Strict** jest **włączona**, następujące warunki powodują błąd w czasie kompilacji:

- Niejawne konwersje zawężające

- Późne wiązanie

- Niejawne wpisanie, które powoduje wystąpienie `Object` typu

  Niejawne Zawężanie błędów konwersji występuje, gdy istnieje niejawna konwersja typu danych, która jest konwersją zawęża. Aby uzyskać więcej informacji, zobacz [Option Strict Statement](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [niejawne i jawne konwersje](https://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66)oraz [rozszerzanie i zwężanie konwersji](https://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).

  Obiekt jest późnie powiązany, gdy jest przypisany do właściwości lub metody zmiennej, która jest zadeklarowana jako typu `Object` . Aby uzyskać więcej informacji, zobacz [Option stricted](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) i [wczesne i późne wiązanie](https://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).

  Niejawne błędy typu obiektu występują, gdy odpowiedni typ nie może zostać wywnioskowany dla zadeklarowanej zmiennej, więc typ `Object` jest wywnioskowany. Dzieje się tak głównie w przypadku używania `Dim` instrukcji w celu deklarowania zmiennej bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz temat [Option Strict Statement](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Wniosking](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)i [Specyfikacja języka Visual Basic](https://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).

  Ustawienie **opcji Strict** odpowiada opcji kompilatora [/optionstrict —](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) .

  Jeśli plik kodu źródłowego zawiera [instrukcję Option Strict](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), `On` `Off` wartość lub w instrukcji zastępuje ustawienie **Option Strict** na **stronie kompilowania**.

  Podczas tworzenia projektu ustawienie **opcji Strict** na **stronie kompilowania** jest ustawione na wartość ustawienia **Strict** w oknie dialogowym **Opcje** . Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie **opcji Strict** w **ustawieniach domyślnych w języku VB** jest **wyłączone**.

  **Opcja rygorystycznych ostrzeżeń indywidualnych.** Sekcja **konfiguracje ostrzeżeń** **strony kompilowania** zawiera ustawienia, które odpowiadają trzem warunkom, które powodują wystąpienie błędu kompilacji, gdy `Option Strict` jest włączony. Poniżej przedstawiono następujące ustawienia:

- **Niejawna konwersja**

- **Późne wiązanie; Wywołanie może zakończyć się niepowodzeniem w czasie wykonywania**

- **Niejawny typ; przyjęto obiekt**

  Jeśli ustawisz **opcję Strict** to **on**, wszystkie trzy z tych ustawień konfiguracyjnych ostrzeżeń mają ustawioną wartość **błąd**. Ustawienie **opcji Strict** to **off**powoduje, że wszystkie trzy ustawienia mają wartość **none**.

  Można indywidualnie zmienić każde ustawienie konfiguracji ostrzegawczej na **none**, **Warning**lub **Error**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżeń mają ustawioną wartość **błąd**, `On` pojawi się w `Option strict` polu. Jeśli wszystkie trzy z nich są ustawione na **Brak**, `Off` pojawia się w tym polu. Dla każdej innej kombinacji tych ustawień pojawia się **(niestandardowe)** .

  **Opcja Porównaj** Określa typ porównywania ciągów, który ma być używany. Wybierz pozycję **Binary** , aby wystawić kompilatorowi użycie binarnego porównania ciągów z uwzględnieniem wielkości liter. Zaznacz **tekst** , aby użyć specyficznych dla ustawień regionalnych porównania ciągów tekstowych.

  To ustawienie odpowiada opcji kompilatora [/optioncompare —](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) .

  Jeśli plik kodu źródłowego zawiera [instrukcję Option Compare](https://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), `Binary` `Text` wartość lub w instrukcji przesłania ustawienie **opcji Porównaj** na **stronie kompilowania**.

  Podczas tworzenia projektu **opcja Porównaj** ustawienia na **stronie kompilowania** jest ustawiona na wartość **opcji Porównaj** ustawienia w oknie dialogowym **Opcje** . Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie **opcji Compare** w **języku VB domyślnie** jest **binarne**.

  **Wnioskowanie dotyczące opcji** Określa, czy zezwalać na wnioskowanie o typie lokalnym w deklaracjach zmiennych. Wybierz opcję **Włącz** , aby zezwolić na korzystanie z wnioskowania o typie lokalnym. Wybierz pozycję **wyłączone** , aby zablokować wnioskowanie o typie lokalnym.

  To ustawienie odpowiada opcji kompilatora [/optioninfer —](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) .

  Jeśli plik kodu źródłowego zawiera [instrukcję opcji wnioskowania](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), `On` `Off` wartość lub w instrukcji przesłania ustawienie **opcji wnioskowania** na **stronie kompilowania**.

  Podczas tworzenia projektu, **opcja wnioskowanie** dla ustawienia na **stronie kompilowania** jest ustawiona na wartość ustawienia wywnioskowania **opcji** w oknie dialogowym **Opcje** . Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie **wnioskowania opcji** w **ustawieniach domyślnych w języku VB** jest **włączone**.

  **Docelowy procesor CPU** Określa procesor, który ma być przeznaczony dla pliku wyjściowego. Określ **x86** dla dowolnego 32-bitowego procesora zgodnego z technologią Intel, **x64** dla 64 każdego procesora zgodnego z technologią Intel, **ARM** dla dowolnego procesora ARM lub **dowolnego procesora** , aby określić, że dowolny procesor jest akceptowalny. **Każdy procesor** jest wartością domyślną dla nowych projektów, ponieważ umożliwia uruchomienie aplikacji na największej liczbie typów sprzętu.

  Aby uzyskać więcej informacji, zobacz [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

  **Preferuj 32-bitowe** Jeśli pole wyboru **Prefer32-bitowy** jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa na 32-bitowej i 64-bitowej wersji systemu Windows. W przeciwnym razie aplikacja działa jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bitowa w systemie 64-bitowe wersje systemu Windows.

  Uruchamianie jako aplikacja 64-bitowa podwaja rozmiar wskaźnika i może spowodować problemy ze zgodnością bibliotek, które są wyłącznie 32-bitowe. Warto uruchomić aplikację jako 64-bitową tylko wtedy, gdy działa znacznie szybciej lub potrzebuje więcej niż 4 GB pamięci.

  To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na **stronie kompilowania** **docelowa Lista procesorów CPU** jest ustawiana na **dowolny procesor**.

- Na **stronie aplikacja**lista **Typ aplikacji** określa, że projekt jest aplikacją.

- Na **stronie aplikacja**lista **platform docelowych** określa .NET Framework 4,5.

  **Konfiguracje ostrzeżeń** Ta tabela zawiera listę warunków kompilacji i odpowiedni poziom powiadomienia dla **każdego z nich,** **Ostrzeżenie**lub **błąd** .

  Domyślnie wszystkie ostrzeżenia kompilatora są dodawane do Lista zadań podczas kompilacji. Wybierz pozycję **Wyłącz wszystkie ostrzeżenia** , aby wystawić kompilatorowi, że nie wystawiasz ostrzeżeń lub błędów. Wybierz pozycję **Traktuj wszystkie ostrzeżenia jako błędy** , jeśli chcesz, aby kompilator traktował ostrzeżenia jako błędy, które muszą zostać naprawione.

  **Wyłącz wszystkie ostrzeżenia** Określa, czy zezwolić kompilatorowi na wydawanie powiadomień zgodnie z opisem w tabeli **warunki i powiadomienia** opisane wcześniej w tym dokumencie. To pole wyboru jest domyślnie wyczyszczone. Zaznacz to pole wyboru, aby spowodować, że kompilator nie wystawia ostrzeżeń lub błędów.

  To ustawienie odpowiada opcji kompilatora [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) .

  **Traktuj wszystkie ostrzeżenia jako błędy** Określa sposób traktowania ostrzeżeń. Domyślnie to pole wyboru jest wyczyszczone, tak aby wszystkie powiadomienia ostrzegawcze pozostawały ustawione na **Ostrzeżenie**. Zaznacz to pole wyboru, aby zmienić wszystkie powiadomienia ostrzegawcze na **błąd**.

  Ta opcja jest dostępna tylko wtedy, gdy polecenie **Wyłącz wszystkie ostrzeżenia** jest wyczyszczone.

  **Generuj plik dokumentacji XML** Określa, czy informacje o dokumentacji mają być generowane. To pole wyboru jest domyślnie zaznaczone, co powoduje, że kompilator generuje informacje o dokumentacji i umieszcza je w pliku XML. Wyczyść to pole wyboru, aby wylecić kompilatorowi nie tworzenie dokumentacji.

  To ustawienie odpowiada opcji kompilatora [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) .

  **Rejestracja w celu** współdziałania z modelem com Określa, czy aplikacja zarządzana będzie uwidaczniać obiekt COM (otoka w modelu COM), która umożliwia obiektowi COM współpracujący z aplikacją.

  Domyślnie to pole wyboru jest wyczyszczone, co oznacza, że aplikacja nie będzie zezwalać na współdziałanie z modelem COM. Zaznacz to pole wyboru, aby zezwolić na współdziałanie modelu COM.

  Ta opcja jest niedostępna dla projektów aplikacji lub aplikacji konsolowych systemu Windows.

  **Zdarzenia kompilacji** Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **zdarzenia kompilacji** . To okno dialogowe służy do określania instrukcji konfiguracji przed kompilacją i po kompilacji dla projektu. To okno dialogowe dotyczy tylko projektów Visual Basic. Aby uzyskać więcej informacji, zobacz [okno dialogowe zdarzenia kompilacji (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

  **Zaawansowane opcje kompilacji** Kliknij ten przycisk, aby uzyskać dostęp do okna dialogowego **Ustawienia AdvancedCompiler** . Okno dialogowe **Ustawienia AdvancedCompiler** służy do określania zaawansowanych właściwości konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko projektów Visual Basic. Aby uzyskać więcej informacji, zobacz okno [dialogowe Zaawansowane ustawienia kompilatora (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Zobacz też
 [Debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [Zarządzanie właściwościami kompilacji](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c) [instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [Visual Basic kompilator wiersza polecenia](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c) [instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)
