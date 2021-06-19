---
title: 'Porady: tworzenie rozwiązania języka właściwego dla domeny'
description: Dowiedz się, jak utworzyć język specyficzny dla domeny (DSL) przy użyciu wyspecjalizowanego Visual Studio rozwiązania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce03349a5179e8dd78220fffd1ff6b21d1a3b495
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387323"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Porady: tworzenie rozwiązania języka właściwego dla domeny
Język specyficzny dla domeny (DSL) jest tworzony przy użyciu wyspecjalizowanego Visual Studio rozwiązania.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tej procedury zainstaluj następujące składniki:

- Visual Studio
- Visual Studio SDK (instalowany w ramach obciążenia **Visual Studio tworzenia rozszerzeń)**
- Zestaw SDK modelowania (zainstalowany jako Visual Studio składnika)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie Domain-Specific językowego

1. Uruchom Kreatora DSL, tworząc **nowy** projektant języka specyficznego dla domeny projektu.

   > [!NOTE]
   > Najlepiej, aby nazwa projektu była prawidłowym identyfikatorem Visual C#, ponieważ może służyć do generowania kodu.

   ::: moniker range="vs-2017"

   ![Okno dialogowe Tworzenie DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Wybierz szablon DSL.

    Na stronie **Domain-Specific opcje** językowe wybierz jeden z szablonów rozwiązań, taki jak **Minimalny język.** Wybierz szablon podobny do DSL, który chcesz utworzyć.

    Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Choosing a Domain-Specific Language Solution Template (Wybieranie szablonu rozwiązania w języku angielskim).](../modeling/choosing-a-domain-specific-language-solution-template.md)

3. Wprowadź rozszerzenie nazwy pliku na **stronie Rozszerzenie** pliku. Powinna być unikatowa w komputerze i na wszystkich komputerach, na których chcesz zainstalować DSL. Powinien zostać wyświetlony komunikat **No applications or Visual Studio editors use this extension**(Żadne aplikacje lub edytory nie używają tego rozszerzenia).

   - Jeśli używasz rozszerzenia nazwy pliku w poprzednich eksperymentalnych językach DSL, które nie zostały w pełni zainstalowane, możesz je wyczyścić za pomocą narzędzia **Reset the Experimental Instance (Resetuj** wystąpienie eksperymentalne), które można znaleźć w menu zestawu VISUAL STUDIO SDK.

   - Jeśli inne Visual Studio, które używa tego rozszerzenia pliku, zostało w pełni zainstalowane na komputerze, rozważ jego odinstalowanie. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń.**

4. Sprawdź pola na pozostałych stronach kreatora i w razie potrzeby dostosuj je. Jeśli ustawienia są satysfakcjonują, kliknij przycisk **Zakończ.** Aby uzyskać więcej informacji na temat ustawień, zobacz [projektant DSL strony kreatora](#settings).

    Kreator tworzy rozwiązanie, które ma dwa projekty o nazwach **Dsl** i **DslPackage.**

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat z alertem, że nie należy uruchamiać szablonów tekstowych z niezaufanych źródeł, kliknij przycisk **OK.** Możesz ustawić, aby ten komunikat nie był ponownie wyświetlany.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> Strony projektant DSL kreatora aplikacji
 Możesz pozostawić kilka pól bez zmian w porównaniu z ich wartościami domyślnymi. Upewnij się jednak, że ustawiono pole Rozszerzenie pliku.

### <a name="solution-settings-page"></a>Strona Ustawienia rozwiązania
 **Na którym szablonie chcesz bazować na języku specyficznym dla domeny?**
Wybierz szablon podobny do DSL, który chcesz utworzyć. Różne szablony zapewniają wygodne punkty początkowe. Po wybraniu szablonu rozwiązania kreator wyświetli opis. Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Choosing a Domain-Specific Language Solution Template (Wybieranie szablonu rozwiązania w języku angielskim).](../modeling/choosing-a-domain-specific-language-solution-template.md)

 **Jak chcesz nazwać język specyficzny dla domeny?**
Wartość domyślna to nazwa rozwiązania. Kod jest generowany na podstawie tej wartości. Musi być prawidłowa jako nazwa klasy języka C#.

### <a name="file-extension-page"></a>Strona Rozszerzenia pliku
 **Jakiego rozszerzenia powinny używać pliki modelu?**
Wpisz nowe rozszerzenie pliku.

 Sprawdź, czy to rozszerzenie pliku nie zostało jeszcze zarejestrowane do użytku na tym komputerze, w następujący sposób:

 Sprawdź w **obszarze Inne narzędzia i aplikacje zarejestrowane do obsługi tego rozszerzenia**. Jeśli zostanie wyświetlony komunikat **No applications or Visual Studio editors use this extension**(Żadne aplikacje lub edytory nie używają tego rozszerzenia), możesz użyć tego rozszerzenia pliku.

 Jeśli zostanie wyświetlona lista narzędzi lub pakietów, wykonaj jedną z następujących czynności:

- Wpisz inne rozszerzenie pliku.

     \- lub —

- Zresetuj Visual Studio wystąpienie eksperymentalne. Spowoduje to wyrejestranie wszystkich wcześniej sbudowaną plików DSL. W menu **Start** kliknij pozycję **Wszystkie** programy , Microsoft Visual Studio **2010 SDK**, **Tools**, a następnie zresetuj wystąpienie programu **Microsoft Visual Studio 2010 Experimental.** Można ponownie skompilować inne pliki DSL, których chcesz użyć ponownie.

     \- lub —

- Jeśli rozszerzenie Visual Studio, które używa tego rozszerzenia pliku, zostało w pełni zainstalowane na komputerze, odinstaluj je. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń.**

### <a name="product-settings-page"></a>Strona Ustawienia produktu
 **Jaka jest nazwa produktu, do którego należy nowy język specyficzny dla domeny?**
Wartość domyślna to nazwa DSL.

 Ta wartość jest używana w Eksplorator Windows (lub Eksplorator plików) do opisywania plików, które mają to rozszerzenie.

 **Jaka jest nazwa firmy, do której należy produkt?**
Nazwa firmy.

 Ta wartość jest uwzględniana we właściwościach AssemblyInfo pakietu DSL.

 **Jaka jest główna przestrzeń nazw dla projektów w tym rozwiązaniu?**
Domyślnie jest to nazwa składająca się z nazwy firmy i produktu.

### <a name="signing-page"></a>Strona podpisywania
 **Tworzenie pliku klucza silnej nazwy** Domyślną opcją jest utworzenie nowego klucza do podpisania zestawu DSL.

 **Użyj istniejącego klucza silnej nazwy** Użyj tej opcji, jeśli chcesz zintegrować DSL z innym zestawem.

 Aby uzyskać więcej informacji na temat silnego nazewnictwa, zobacz [Creating and Using Strong-Named Assemblies](/dotnet/standard/assembly/create-use-strong-named)(Tworzenie i używanie Strong-Named zestawów).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))