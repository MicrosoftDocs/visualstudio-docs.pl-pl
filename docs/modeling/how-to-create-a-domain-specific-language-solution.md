---
title: 'Porady: tworzenie rozwiązania języka właściwego dla domeny'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 844f3eb97ed9e07aa8125688d2bfe8944249b008
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541794"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Porady: tworzenie rozwiązania języka właściwego dla domeny
Język specyficzny dla domeny (DSL) jest tworzony przy użyciu wyspecjalizowanego rozwiązania programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tej procedury należy zainstalować następujące składniki:

- Visual Studio
- Visual Studio SDK (instalowany jako część obciążenia **programistycznego rozszerzenia programu Visual Studio** )
- Modeling SDK (instalowany jako składnik programu Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania dotyczącego języka specyficznego dla domeny

1. Uruchom Kreatora DSL, tworząc nowy projekt **Projektant języka specyficznego dla domeny** .

   > [!NOTE]
   > Zaleca się, aby nazwa wybrana dla projektu była prawidłowym identyfikatorem języka Visual C#, ponieważ może służyć do generowania kodu.

   ::: moniker range="vs-2017"

   ![Utwórz okno dialogowe DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Wybierz szablon DSL.

    Na stronie **Wybieranie opcji języka specyficznego dla domeny** wybierz jeden z szablonów rozwiązań, takich jak **minimalny język**. Wybierz szablon, który jest podobny do DSL, które chcesz utworzyć.

    Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Wprowadź rozszerzenie nazwy pliku na stronie **rozszerzenia pliku** . Powinna być unikatowa w komputerze i na wszystkich komputerach, na których ma zostać zainstalowana linia DSL. Powinien zostać wyświetlony komunikat **Brak aplikacji lub edytorów programu Visual Studio korzystających z tego rozszerzenia**.

   - Jeśli użyto rozszerzenia nazwy pliku w poprzedniej eksperymentalnej językami DSL, która nie została w pełni zainstalowana, można je usunąć za pomocą narzędzia **Zresetuj wystąpienie eksperymentalne** , które można znaleźć w menu zestawu SDK programu Visual Studio.

   - Jeśli inne rozszerzenie programu Visual Studio, które używa tego rozszerzenia pliku, zostało w pełni zainstalowane na komputerze, rozważ odinstalowanie go. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

4. Należy sprawdzić i w razie potrzeby dostosować pola na pozostałych stronach kreatora. Gdy ustawienia zostaną spełnione, kliknij przycisk **Zakończ**. Aby uzyskać więcej informacji na temat ustawień, zobacz [Projektant DSL strony kreatora](#settings).

    Kreator tworzy rozwiązanie, które ma dwa projekty o nazwie **DSL** i **DslPackage**.

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat z alertami, że nie chcesz uruchamiać szablonów tekstowych z niezaufanych źródeł, kliknij przycisk **OK**. Możesz ustawić ten komunikat, aby nie pojawiał się ponownie.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a>Strony kreatora projektant DSL
 Można pozostawić kilka pól niezmienionych z wartości domyślnych. Należy jednak upewnić się, że pole rozszerzenie pliku jest ustawione.

### <a name="solution-settings-page"></a>Strona Ustawienia rozwiązania
 **Który szablon ma być oparty na języku specyficznym dla domeny?**
Wybierz szablon, który jest podobny do DSL, które chcesz utworzyć. Różne szablony zapewniają wygodne punkty startowe. Po wybraniu szablonu rozwiązania Kreator wyświetli opis. Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Jak chcesz nazwać język specyficzny dla domeny?**
Wartość domyślna to nazwa rozwiązania. Kod jest generowany na podstawie tej wartości. Musi być prawidłowy jako nazwa klasy C#.

### <a name="file-extension-page"></a>Strona rozszerzenia pliku
 **Jakiego rozszerzenia powinny używać pliki modelu?**
Wpisz nowe rozszerzenie pliku.

 Sprawdź, czy to rozszerzenie pliku nie zostało jeszcze zarejestrowane do użycia na tym komputerze w następujący sposób:

 Zapoznaj **się z innymi narzędziami i aplikacjami zarejestrowanymi do obsługi tego rozszerzenia**. Jeśli zobaczysz komunikat **Brak aplikacji lub edytorów programu Visual Studio korzystających z tego rozszerzenia**, możesz użyć tego rozszerzenia pliku.

 Jeśli zostanie wyświetlona lista narzędzi lub pakietów, należy wykonać jedną z następujących czynności:

- Wpisz inne rozszerzenie pliku.

     \-oraz

- Zresetuj wystąpienie eksperymentalne programu Visual Studio. Spowoduje to Wyrejestrowanie wszystkich utworzonych wcześniej językami DSL. W menu **Start** kliknij pozycję **wszystkie programy**, **Microsoft Visual Studio zestaw SDK 2010**, **Narzędzia**, a następnie **Zresetuj wystąpienie eksperymentalne Microsoft Visual Studio 2010**. Możesz ponownie skompilować wszystkie inne językami DSL, których chcesz użyć.

     \-oraz

- Jeśli rozszerzenie programu Visual Studio, które używa tego rozszerzenia pliku, zostało w pełni zainstalowane na komputerze, odinstaluj je. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

### <a name="product-settings-page"></a>Strona Ustawienia produktu
 **Jaka jest nazwa produktu, do którego należy nowy język specyficzny dla domeny?**
Wartość domyślna to nazwa DSL.

 Ta wartość jest używana w Eksploratorze Windows (lub Eksploratorze plików) do opisywania plików, które mają to rozszerzenie pliku.

 **Jaka jest nazwa firmy, do której należy produkt?**
Nazwa firmy.

 Ta wartość jest dołączana do właściwości AssemblyInfo pakietu DSL.

 **Jaka jest główna przestrzeń nazw dla projektów w tym rozwiązaniu?**
Ta wartość domyślna to nazwa składająca się z nazwy firmy i produktów.

### <a name="signing-page"></a>Strona podpisywania
 **Utwórz plik klucza o silnej nazwie** Opcja domyślna to utworzenie nowego klucza w celu podpisania zestawu DSL.

 **Użyj istniejącego klucza silnej nazwy** Użyj tej opcji, jeśli chcesz zintegrować DSL z innym zestawem.

 Aby uzyskać więcej informacji na temat silnego nazewnictwa, zobacz [Tworzenie i używanie zestawów o silnej nazwie](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
