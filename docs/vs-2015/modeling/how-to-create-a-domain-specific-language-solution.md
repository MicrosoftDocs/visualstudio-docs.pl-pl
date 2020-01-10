---
title: 'Instrukcje: Tworzenie rozwiązania dotyczącego języka specyficznego dla domeny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4c5bd99c47517156f1ec89de9da1a163223b99a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850437"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Porady: tworzenie rozwiązania języka właściwego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język specyficzny dla domeny (DSL) jest tworzony przy użyciu wyspecjalizowanego rozwiązania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="prerequisites"></a>Wymagania wstępne
 Przed rozpoczęciem tej procedury należy najpierw zainstalować następujące składniki:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|{1&gt;{2&gt;Visual Studio Visualisation i Modeling SDK&lt;2}&lt;1}|[http://go.microsoft.com/fwlink/?LinkID=185581](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania dotyczącego języka specyficznego dla domeny

#### <a name="to-create-a-domain-specific-language-solution"></a>Aby utworzyć rozwiązanie dla języka specyficznego dla domeny

1. Uruchom Kreatora DSL.

   1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

   2. **Nowy projekt** pojawi się okno dialogowe.

   3. W obszarze **typy projektów**rozwiń węzeł **Inne typy projektów** , a następnie kliknij pozycję **rozszerzalność**.

   4. Kliknij **Projektant języka specyficznego dla domeny**.

   5. W polu **Nazwa** wpisz nazwę rozwiązania. Kliknij przycisk **OK**.

       Zostanie wyświetlony **kreator Projektant języka specyficznego dla domeny** .

      > [!NOTE]
      > Najlepiej, gdy wpisana nazwa powinna być prawidłowym identyfikatorem wizualizacji C# , ponieważ może służyć do generowania kodu.

      ![Utwórz okno dialogowe DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")

2. Wybierz szablon DSL.

    Na stronie **Wybieranie opcji języka specyficznego dla domeny** wybierz jeden z szablonów rozwiązań, takich jak **minimalny język**. Wybierz szablon, który jest podobny do DSL, które chcesz utworzyć.

    Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Wprowadź rozszerzenie nazwy pliku na stronie **rozszerzenia pliku** . Powinna być unikatowa w komputerze i na wszystkich komputerach, na których ma zostać zainstalowana linia DSL. Powinien zostać wyświetlony komunikat **Brak aplikacji lub edytorów programu Visual Studio korzystających z tego rozszerzenia**.

   - Jeśli użyto rozszerzenia nazwy pliku w poprzedniej eksperymentalnej językami DSL, która nie została w pełni zainstalowana, można je usunąć za pomocą narzędzia **Zresetuj wystąpienie eksperymentalne** , które można znaleźć w menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK.

   - Jeśli inne rozszerzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], które używa tego rozszerzenia pliku, zostało w pełni zainstalowane na komputerze, rozważ odinstalowanie go. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

4. Należy sprawdzić i w razie potrzeby dostosować pola na pozostałych stronach kreatora. Gdy ustawienia zostaną spełnione, kliknij przycisk **Zakończ**. Aby uzyskać więcej informacji na temat ustawień, zobacz [Projektant DSL strony kreatora](#settings).

    Kreator tworzy rozwiązanie, które ma dwa projekty o nazwie **DSL** i **DslPackage**.

   > [!NOTE]
   > Jeśli zostanie wyświetlony komunikat z alertami, że nie chcesz uruchamiać szablonów tekstowych z niezaufanych źródeł, kliknij przycisk **OK**. Możesz ustawić ten komunikat, aby nie pojawiał się ponownie.

## <a name="settings"></a>Strony kreatora projektant DSL
 Można pozostawić kilka pól niezmienionych z wartości domyślnych. Należy jednak upewnić się, że pole rozszerzenie pliku jest ustawione.

### <a name="solution-settings-page"></a>Strona Ustawienia rozwiązania
 **Który szablon ma być oparty na języku specyficznym dla domeny?**
Wybierz szablon, który jest podobny do DSL, które chcesz utworzyć. Różne szablony zapewniają wygodne punkty startowe. Po wybraniu szablonu rozwiązania Kreator wyświetli opis. Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Jak chcesz nazwać język specyficzny dla domeny?**
Wartość domyślna to nazwa rozwiązania. Kod jest generowany na podstawie tej wartości. Musi być prawidłową nazwą C# klasy.

### <a name="file-extension-page"></a>Strona rozszerzenia pliku
 **Jakiego rozszerzenia powinny używać pliki modelu?**
Wpisz nowe rozszerzenie pliku.

 Sprawdź, czy to rozszerzenie pliku nie zostało jeszcze zarejestrowane do użycia na tym komputerze w następujący sposób:

 Zapoznaj **się z innymi narzędziami i aplikacjami zarejestrowanymi do obsługi tego rozszerzenia**. Jeśli zobaczysz komunikat **Brak aplikacji lub edytorów programu Visual Studio korzystających z tego rozszerzenia**, możesz użyć tego rozszerzenia pliku.

 Jeśli zostanie wyświetlona lista narzędzi lub pakietów, należy wykonać jedną z następujących czynności:

- Wpisz inne rozszerzenie pliku.

     \- lub —

- Zresetuj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wystąpienie eksperymentalne. Spowoduje to Wyrejestrowanie wszystkich utworzonych wcześniej językami DSL. W menu **Start** kliknij pozycję **wszystkie programy**, **Microsoft Visual Studio zestaw SDK 2010**, **Narzędzia**, a następnie **Zresetuj wystąpienie eksperymentalne Microsoft Visual Studio 2010**. Możesz ponownie skompilować wszystkie inne językami DSL, których chcesz użyć.

     \- lub —

- Jeśli rozszerzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], które używa tego rozszerzenia pliku, zostało w pełni zainstalowane na komputerze, odinstaluj je. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

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

 Aby uzyskać więcej informacji na temat silnego nazewnictwa, zobacz [Tworzenie i używanie zestawów o silnej nazwie](https://docs.microsoft.com/dotnet/standard/assembly/create-use-strong-named?redirectedfrom=MSDN).

## <a name="see-also"></a>Zobacz też
 Jak zdefiniować [słownik narzędzia języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) [w języku specyficznym dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
