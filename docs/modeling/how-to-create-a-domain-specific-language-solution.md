---
title: 'Instrukcje: Tworzenie rozwiązania języka specyficznego dla domeny'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac8a47aeca8875dabe3fdf388e9a73d68ec514e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445207"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Instrukcje: Tworzenie rozwiązania języka specyficznego dla domeny
Języka specyficznego dla domeny (DSL) jest tworzony przy użyciu specjalnych rozwiązania programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tej procedury należy zainstalować następujące składniki:

- Visual Studio
- Visual Studio SDK (instalowany jako część **programowanie rozszerzeń programu Visual Studio** obciążenia)
- Modeling SDK (zainstalowany jako składnik Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania języka dotyczącego określonej domeny

1. Uruchom Kreatora DSL przez utworzenie nowego **projektanta języka specyficznego dla domeny** projektu.

   > [!NOTE]
   > Najlepiej, nazwę i wybierz dla projektu powinna być prawidłową Visual C# identyfikator ponieważ mogą być używane do generowania kodu.

   ::: moniker range="vs-2017"

   ![Tworzenie okna dialogowego DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Wybierz szablon DSL.

    Na **wybierz opcje języka specyficznego dla domeny** wybierz jeden z szablonów rozwiązań, takich jak **minimalny języka**. Wybierz szablon, który przypomina język DSL, który chcesz utworzyć.

    Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Wprowadź rozszerzenie nazwy pliku na **rozszerzenie pliku** strony. Powinien on być unikatowy w komputerze i w każdym komputerze, na którym chcesz zainstalować język DSL. Powinien zostać wyświetlony komunikat **Brak aplikacji lub edytorów programu Visual Studio za pomocą tego rozszerzenia**.

   - Jeśli rozszerzenie nazwy pliku jest używany, poprzednie eksperymentalne językami DSL, które nie zostały w pełni zainstalowane, można wyczyścić je na zewnątrz przy użyciu **Zresetuj wystąpienie eksperymentalne** narzędzia, które znajdują się w menu programu Visual Studio SDK.

   - Jeśli inny rozszerzenie programu Visual Studio, która używa tego rozszerzenia pliku pełni zainstalowaną na komputerze, należy rozważyć odinstalowanie go. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.

4. Zbadaj i w razie potrzeby dostosować, pola na pozostałych stronach kreatora. Gdy jesteś zadowolony z ustawień, kliknij przycisk **Zakończ**. Aby uzyskać więcej informacji na temat ustawień, zobacz [stron kreatora Projektant DSL](#settings).

    Kreator utworzy rozwiązanie, które ma dwa projekty, które noszą nazwy **Dsl** i **DslPackage**.

   > [!NOTE]
   > Jeśli zobaczysz komunikat z ostrzeżeniem, nie można uruchomić szablony tekstowe ze źródeł niezaufanych, kliknij przycisk **OK**. Można ustawić ten komunikat, aby nie pojawiają się ponownie.

## <a name="settings"></a> Na stronach kreatora projektanta DSL
 Możesz pozostawić kilka pól, bez zmian wartości domyślne. Jednak należy się upewnić, czy ustawić pola rozszerzenie pliku.

### <a name="solution-settings-page"></a>Strona Ustawienia rozwiązania
 **Szablon, który chcesz utworzyć swoje języka właściwego dla domeny na?**
Wybierz szablon, który przypomina język DSL, który chcesz utworzyć. Różne szablony zapewniają wygodny punktów początkowych. Po wybraniu szablonu rozwiązania, Kreator wyświetli opis. Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Co chcesz nazwać języka dotyczącego określonej domeny?**
Wartość domyślna to nazwa rozwiązania. Kod jest generowany na podstawie tej wartości. Musi być prawidłowy, jak nazwa klasy C#.

### <a name="file-extension-page"></a>Strona rozszerzenie pliku
 **Jakie rozszerzenia mają używać pliki modelu?**
Wpisz nowe rozszerzenie pliku.

 Sprawdź, czy to rozszerzenie pliku nie już został zarejestrowany do użycia w tym komputerze, w następujący sposób:

 Sprawdź w obszarze **inne narzędzia i aplikacje zarejestrowane w celu obsługi tego rozszerzenia**. Jeśli zostanie wyświetlony komunikat **Brak aplikacji lub edytorów programu Visual Studio za pomocą tego rozszerzenia**, wówczas można użyć tego rozszerzenia pliku.

 Jeśli zobaczysz listę narzędzi lub pakietów, należy wykonać jedną z następujących czynności:

- Wpisz rozszerzenie inny plik.

     \- lub —

- Zresetuj wystąpienie eksperymentalne programu Visual Studio. To wyrejestruje wszystkich języków DSL, które zostały wcześniej utworzone. Na **Start** menu, kliknij przycisk **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, a następnie **resetowania Microsoft Visual Studio 2010 doświadczalne wystąpienie**. Można odtworzyć innych języków, które chcesz ponownie użyć DSL.

     \- lub —

- Jeśli rozszerzenia Visual Studio, która używa tego rozszerzenia pliku została w pełni zainstalowana na komputerze, należy ją odinstalować. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.

### <a name="product-settings-page"></a>Strona ustawień produktu
 **Co to jest nazwa produktu, którego należy nowy język specyficznego dla domeny?**
Wartość domyślna to nazwa języka DSL.

 Ta wartość jest używana w Eksploratorze Windows (lub Eksploratora plików) do opisywania plików mających rozszerzenie tego pliku.

 **Co to jest nazwa firmy, której należy produkt?**
Nazwę swojej firmy.

 Ta wartość jest włączona do właściwości AssemblyInfo pakietu języka DSL.

 **Co to jest główna przestrzeń nazw dla projektów w tym rozwiązaniu?**
Domyślnie jest nazwą składającą się z Twojej firmy i nazwy produktu.

### <a name="signing-page"></a>Strona podpisywania
 **Utwórz plik klucza o silnej nazwie** opcją domyślną jest utworzenie nowego klucza do podpisywania zestawu DSL.

 **Użyj istniejącego klucza o silnej nazwie** Użyj tej opcji, jeśli chcesz zintegrować DSL za pomocą innego zestawu.

 Aby uzyskać więcej informacji o silnych nazwach, zobacz [tworzenie i zestawy Using Strong-Named](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
