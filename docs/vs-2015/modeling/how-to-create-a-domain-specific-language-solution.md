---
title: 'Instrukcje: Tworzenie rozwiązania języka dotyczącego określonej domeny | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eae08b771f3bd5748485f9029f7f12725df6f28f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698135"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Instrukcje: Tworzenie rozwiązania języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Języka specyficznego dla domeny (DSL) jest tworzony przy użyciu wyspecjalizowanego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed rozpoczęciem tej procedury, należy najpierw zainstalować te składniki:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualisation i Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania języka dotyczącego określonej domeny  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Tworzenie rozwiązań języka dotyczącego określonej domeny  
  
1. Uruchom Kreatora DSL.  
  
   1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
   2. **Nowy projekt** pojawi się okno dialogowe.  
  
   3. W obszarze **typów projektów**, rozwiń węzeł **inne typy projektów** węzeł, a następnie kliknij przycisk **rozszerzalności**.  
  
   4. Kliknij przycisk **projektanta języka specyficznego dla domeny**.  
  
   5. W **nazwa** wpisz nazwę dla rozwiązania. Kliknij przycisk **OK**.  
  
       **Kreator projektanta języka specyficznego dla domeny** pojawia się.  
  
      > [!NOTE]
      > Najlepiej możesz wpisać nazwę powinny być prawidłowym Visual C# identyfikatorem, ponieważ może służyć do generowania kodu.  
  
      ![Tworzenie okna dialogowego DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. Wybierz szablon DSL.  
  
    Na **wybierz opcje języka specyficznego dla domeny** wybierz jeden z szablonów rozwiązań, takich jak **minimalny języka**. Wybierz szablon, który przypomina język DSL, który chcesz utworzyć.  
  
    Aby uzyskać więcej informacji na temat szablonów rozwiązań, zobacz [Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3. Wprowadź rozszerzenie nazwy pliku na **rozszerzenie pliku** strony. Powinien on być unikatowy w komputerze i w każdym komputerze, na którym chcesz zainstalować język DSL. Powinien zostać wyświetlony komunikat **Brak aplikacji lub edytorów programu Visual Studio za pomocą tego rozszerzenia**.  
  
   - Jeśli rozszerzenie nazwy pliku jest używany, poprzednie eksperymentalne językami DSL, które nie zostały w pełni zainstalowane, można wyczyścić je na zewnątrz przy użyciu **Zresetuj wystąpienie eksperymentalne** narzędzia, które znajdują się w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menu zestawu SDK.  
  
   - Jeśli w kolejnym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pełni zainstalowano rozszerzenie, która używa tego rozszerzenia pliku na komputerze, należy rozważyć odinstalowanie go. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.  
  
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
  
- Resetuj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wystąpienie eksperymentalne. To wyrejestruje wszystkich języków DSL, które zostały wcześniej utworzone. Na **Start** menu, kliknij przycisk **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, a następnie **resetowania Microsoft Visual Studio 2010 doświadczalne wystąpienie**. Można odtworzyć innych języków, które chcesz ponownie użyć DSL.  
  
     \- lub —  
  
- Jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pełni zainstalowano rozszerzenie, która używa tego rozszerzenia pliku na komputerze, odinstaluj je. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.  
  
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
 **Utwórz plik klucza o silnej nazwie**  
 Jest to opcja domyślna można utworzyć nowego klucza do podpisywania zestawu DSL.  
  
 **Użyj istniejącego klucza o silnej nazwie**  
 Użyj tej opcji, jeśli chcesz zintegrować DSL za pomocą innego zestawu.  
  
 Aby uzyskać więcej informacji o silnych nazwach, zobacz [tworzenie i zestawy Using Strong-Named](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Zobacz też  
 [Jak zdefiniować języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   
 [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
