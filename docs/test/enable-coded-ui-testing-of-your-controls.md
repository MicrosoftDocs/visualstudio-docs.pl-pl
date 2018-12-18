---
title: Włącz testowanie kodowanego interfejsu użytkownika dla Twoich kontrolek
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b9f9256407f854e5e7eefbca0cdd767679b9c88c
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895954"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek

Implementuje obsługę kodowanych testów interfejsu użytkownika framework się bardziej sprawdzalnego działa zgodnie z kontroli. Zwiększa poziom obsługi można dodać przyrostowo. Rozpocznij dzięki obsłudze rekordu i odtwarzania oraz właściwości sprawdzania poprawności. Następnie kompilacji na tym, aby umożliwić konstruktora kodowanego testu interfejsu użytkownika, rozpoznawał właściwości niestandardowych kontroli nad. Podaj niestandardowe klasy dostęp do tych właściwości z wygenerowanego kodu. Może również pomóc kodowanego interfejsu użytkownika testu konstruktora przechwytywania akcje w sposób, który jest bliżej celem akcji rejestrowane.

![CUIT&#95;pełne](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Obsługuje rekordu i odtwarzania oraz właściwości sprawdzania poprawności poprzez implementację ułatwień dostępu

Konstruktor kodowanego testu interfejsu użytkownika przechwytuje informacji na temat formantów napotka podczas rejestrowania i następnie generuje kod w celu odtworzenia tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, kodowanego testu interfejsu użytkownika przechwytuje akcji (takich jak kliknięcia myszą) za pomocą współrzędnych ekranu. Podczas odtwarzania testu wygenerowany kod uruchamia akcje w takich samych współrzędnych ekranu. Jeśli formant znajduje się w innym miejscu na ekranie, podczas odtwarzania testu, wygenerowany kod zakończy się niepowodzeniem do wykonania akcji. Wdrażając nie ułatwień dostępu dla kontrolki, może zostać wyświetlony niepowodzenia testu, jeśli test jest odtwarzany na ekranach o różnych konfiguracjach, w różnych środowiskach, lub gdy zmienia się układ interfejsu użytkownika.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

 W przypadku zaimplementowania ułatwień dostępu kodowanego testu interfejsu użytkownika używa, do przechwytywania informacji na temat kontrolki, gdy rejestruje testu. Następnie po uruchomieniu testu, wygenerowany kod będzie oparte na metodzie powtórzeń tych zdarzeń dla formantu, nawet jeśli jest on gdzieś w interfejsie użytkownika. Autorzy testów można również utworzyć potwierdza przy użyciu podstawowe właściwości formantu.

 ![CUIT&#95;rekordu](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Do obsługi rekord i odtwarzania, właściwości sprawdzania poprawności i nawigacji dla formantu Windows Forms
 Implementowanie ułatwień dostępu dla kontrolki, co zostało opisane w poniższej procedurze, a omówiona szczegółowo w <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;dostępne](../test/media/cuit_accessible.png)

1.  Implementowanie klasy, która pochodzi od klasy <xref:System.Windows.Forms.Control.ControlAccessibleObject>i zastępowania <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwości, aby zwrócić obiekt klasy.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2.  Zastąp dostępnego obiektu <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> i <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> właściwości i metody.

3.  Implementowanie innego obiektu ułatwień dostępu dla kontrolki podrzędnej i przesłonić kontrolki podrzędnej <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwość zwracaj obiekt w ułatwienia dostępu.

4.  Zastąp <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, i <xref:System.Windows.Forms.AccessibleObject.Select%2A> właściwości i metody dla obiektu ułatwień dostępu kontrolki podrzędnej.

> [!NOTE]
> W tym temacie, który rozpoczyna się od przykładu ułatwień dostępu w <xref:System.Windows.Forms.AccessibleObject>i następnie opiera się na tym przykładzie pozostały procedur. Jeśli chcesz utworzyć działającą wersją próbki ułatwień dostępu, tworzenie aplikacji konsolowej, a następnie Zastąp kod w *Program.cs* z przykładowym kodem. Dodaj odwołania do ułatwień dostępu, System.Drawing i przestrzeń nazw System.Windows.Forms. Zmiana **Osadź typy współdziałania** ułatwień dostępu do **False** , aby wyeliminować ostrzeżenia kompilacji. Można zmienić typu danych wyjściowych projektu z **aplikację Konsolową** do **aplikacji Windows** okno konsoli nie będą wyświetlane po uruchomieniu aplikacji.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Obsługuje sprawdzanie poprawności właściwości niestandardowej poprzez implementację dostawcy właściwości

Po zaimplementowaniu podstawowa pomoc techniczna dla rekordu i odtwarzania oraz właściwości sprawdzania poprawności można udostępnić kontroli nad właściwości niestandardowych do zakodowanych testów interfejsu użytkownika poprzez implementację <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> wtyczki. Na przykład poniższa procedura tworzy dostawcy właściwości, który umożliwia kodowane testy interfejsu użytkownika do dostępu do właściwości stanu formantów podrzędnych CurveLegend formant wykresu:

 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Do obsługi sprawdzania poprawności właściwości niestandardowej

![CUIT&#95;właściwości](../test/media/cuit_props.png)

1. Zastąpienie krzywej legendy dostępne obiektu <xref:System.Windows.Forms.AccessibleObject.Description%2A> właściwości, aby przekazać wartości właściwości sformatowanego ciągu opisu. Wiele wartości należy rozdzielić średnikami (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Utwórz pakiet rozszerzenia testów interfejsu użytkownika dla kontrolki przez tworzenie projektu biblioteki klas. Dodaj odwołania do ułatwień dostępu, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common i Microsoft.VisualStudio.TestTools.Extension. Zmiana **Osadź typy współdziałania** ułatwień dostępu do **False**.

1. Dodaj klasę dostawcy właściwość, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Implementowanie dostawcy właściwości przez umieszczenie nazwy i właściwości deskryptorów właściwości w <xref:System.Collections.Generic.Dictionary%602>.

1. Zastąp <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> do wskazania, że zestaw obsługuje specyficznej dla kontroli formantu i jego elementy podrzędne.

1. Zastąp pozostałe metody abstrakcyjne klasy <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Dodaj klasę pakietu rozszerzenia, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Zdefiniuj `UITestExtensionPackage` atrybutu dla zestawu.

1. W klasie pakietu rozszerzenia, należy zastąpić <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> do zwrócenia klasa dostawcy właściwości, gdy dostawca właściwości.

1. Zastąp pozostałe metody abstrakcyjne i właściwości działania <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Tworzenie plików binarnych i skopiować je do *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Ten pakiet rozszerzenia jest stosowany do żadnego formantu, który jest typu "Text". Jeśli testujesz wielu formantów tego samego typu, Testuj je oddzielnie, dzięki czemu można zarządzać pakietów rozszerzeń, które są wdrażane po zarejestrowaniu testów.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Obsługuje generowanie kodu poprzez implementację klasy, uzyskiwania dostępu do właściwości niestandardowych

Gdy kodowanego testu interfejsu użytkownika generuje kod z nagrania sesji, używa <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> klasy, aby dostęp do kontrolek.

Jeśli zastało zaimplementowane Dostawca właściwości w celu zapewnienia dostępu do właściwości niestandardowych kontroli nad, można dodać klas wyspecjalizowanych, który służy do uzyskiwania dostępu do tych właściwości. Dodawanie klas wyspecjalizowanych upraszcza wygenerowanego kodu.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać klas wyspecjalizowanych do usługi kontroli dostępu

![CUIT&#95;generowanie kodu](../test/media/cuit_codegen.png)

1. Implementuje klasę, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> i dodać do kolekcji właściwości wyszukiwania w Konstruktorze typ formantu.

1. Implementuje właściwości niestandardowe kontroli nad jako właściwości klasy.

1. Twój dostawca właściwości zastąpienia <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodę, aby zwracany typ nową klasę dla krzywej z formantów podrzędnych legendy.

1. Twój dostawca właściwości zastąpienia <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodę, aby zwracany typ metody PropertyNames nowej klasy.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Obsługuje świadomie akcji przez zaimplementowanie filtr akcji

 Visual Studio zapisuje testu, umożliwia przechwytywanie każdego zdarzenia myszy i klawiatury. Jednak w niektórych przypadkach celem akcji mogą zostać utracone w serii zdarzeń klawiatury oraz myszy. Na przykład jeśli formant obsługuje autouzupełniania, ten sam zestaw zdarzeń klawiatury oraz myszy może spowodować naliczenie inną wartość, gdy test jest odtwarzany w innym środowisku. Możesz dodać filtr akcji z wtyczki zastępuje serii zdarzeń klawiatury oraz myszy przy użyciu jednej akcji. W ten sposób można zastąpić serii zdarzeń klawiatury oraz myszy, wybranych wartości za pomocą jednej akcji, która ustawia wartości. Tą operacją chroni kodowane testy interfejsu użytkownika z różnic w funkcji autouzupełniania z jednego środowiska do innego.

### <a name="to-support-intent-aware-actions"></a>Aby obsługiwać świadomie akcje

![CUIT&#95;akcji](../test/media/cuit_actions.png)

1. Implementowanie klasy filtru akcji, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, zastępowanie właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> i <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.

1. Zastąp <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. W tym przykładzie zastępuje akcji kliknij dwukrotnie plik przy użyciu akcji jednym kliknięciem.

1. Dodawanie filtru akcji <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> metoda pakietu rozszerzenia.

1. Tworzenie plików binarnych i skopiować je do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Filtr akcji zależy od implementacji dostępności lub Dostawca właściwości.

## <a name="debug-your-property-provider-or-action-filter"></a>Debugowanie filtru akcji lub dostawcy właściwości

Właściwości filtru akcji i dostawcy są implementowane w pakiecie rozszerzenia. Konstruktor testu jest uruchamiany pakiet rozszerzenia w oddzielnym procesie z aplikacji.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować filtru akcji lub dostawcy właściwości

1.  Tworzenie wersji debugowania kopii pakietu rozszerzenia *.dll* i *.pdb* plików *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2.  Uruchom aplikację (nie w debugerze).

3.  Uruchamianie kodowanego testu interfejsu użytkownika.

     `codedUITestBuilder.exe  /standalone`

4.  Dołącz debuger do procesu codedUITestBuilder.

5.  Ustaw punkty przerwania w kodzie.

6.  Konstruktor kodowanego testu interfejsu użytkownika tworzenia potwierdza wykonywania dostawcy właściwości i Rejestruj akcje do wykonywania filtrów akcji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.AccessibleObject>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)