---
title: Wybierz elementy paska narzędzi, składniki WPF
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 731fe05e90e01c60f0a7ff3a14917d6d7625bc1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570560"
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybieranie elementów przybornika, składniki WPF

Na tej karcie okna dialogowego **Wybieranie elementów przybornika** jest wyświetlana lista kontrolek Programu Windows Presentation Foundation (WPF) dostępnych na komputerze lokalnym. Aby wyświetlić tę listę, wybierz polecenie **Wybierz elementy przybornika** z menu **Narzędzia,** aby wyświetlić okno dialogowe **Wybieranie elementów przybornika,** a następnie wybierz kartę **Składniki WPF.** Aby posortować wymienione komponenty, zaznacz dowolny nagłówek kolumny.

- Po zaznaczeniu pola wyboru obok komponentu w **przyborniku**zostanie wyświetlona ikona tego komponentu .

    > [!TIP]
    > Aby dodać kontrolkę WPF do dokumentu projektu, który jest otwarty do edycji, przeciągnij jego ikonę **przybornika** na powierzchnię widoku Projekt. Domyślne znaczniki i kod składnika są wstawiane do projektu, gotowe do zmodyfikowania. Aby uzyskać więcej informacji, zobacz [Przybornik](../../ide/reference/toolbox.md).

- Gdy pole wyboru obok komponentu zostanie wyczyszczone, odpowiednia ikona zostanie usunięta z **przybornika**.

    > [!NOTE]
    > Składniki .NET zainstalowane na komputerze pozostają dostępne niezależnie od tego, czy ikony dla nich są wyświetlane w **przyborniku**.

Kolumny na karcie **Składniki WPF** zawierają następujące informacje:

**Nazwa**

Wyświetla nazwy formantów WPF, dla których istnieją wpisy w rejestrze komputera.

**Namespace**

Wyświetla hierarchię obszaru nazw [interfejsu API platformy .NET,](/dotnet/api/?view=netframework-4.7) który definiuje strukturę składnika. Sortuj w tej kolumnie, aby wyświetlić listę dostępnych składników w każdej przestrzeni nazw platformy .NET zainstalowanej na komputerze.

**Nazwa zestawu**

Wyświetla nazwę zestawu .NET zawierającego obszar nazw dla każdego składnika. Sortuj w tej kolumnie, aby wyświetlić listę obszarów nazw zawartych w każdym zestawie .NET zainstalowanym na komputerze.

**Katalog**

Wyświetla lokalizację złożenia .NET. Domyślną lokalizacją dla wszystkich zestawów jest globalna pamięć podręczna zestawów. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej zestawów, zobacz [Praca z zestawami i globalna pamięć podręczna zestawów](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista elementów UI

### <a name="filter"></a>Filtr

Filtruje listę formantów WPF na podstawie ciągu, który można podać w polu tekstowym. Zostaną wyświetlone wszystkie dopasowania z dowolnej z czterech kolumn.

**Clear**

Czyści ciąg filtru.

**Przeglądaj**

Otwiera okno dialogowe **Otwórz,** które umożliwia przechodzenie do zestawów zawierających formanty WPF. Służy do ładowania zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.

**Język**

Pokazuje zlokalizowany język zestawu, który zawiera wybrany formant WPF.

## <a name="limitations"></a>Ograniczenia

Dodawanie formantu <xref:System.Windows.Controls.UserControl> niestandardowego lub do przybornika ma następujące ograniczenia:

- Działa tylko dla formantów niestandardowych zdefiniowanych poza bieżącym projektem.

- Nie aktualizuje się poprawnie po zmianie konfiguracji rozwiązania z Debugowania na Wydanie lub z release na Debug. Jest tak, ponieważ odwołanie nie jest odwołaniem do projektu, ale jest dla zestawu na dysku zamiast tego. Jeśli formant jest częścią bieżącego rozwiązania, po zmianie z debugowania na release, projekt kontynuuje odwoływanie się do wersji debugowania formantu.

Ponadto jeśli metadane w czasie projektowania są stosowane do formantu niestandardowego i te metadane określa, że [microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) jest ustawiona na `false`, formant nie pojawia się w przyborniku.

Formanty można odwoływać się bezpośrednio w widoku XAML, mapując obszar nazw i zestaw dla formantu.

## <a name="see-also"></a>Zobacz też

- [Przybornik](../../ide/reference/toolbox.md)
- [Rozpoczynanie pracy z aparatem WPF](../../designers/getting-started-with-wpf.md)
