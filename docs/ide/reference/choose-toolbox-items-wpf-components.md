---
title: Wybierz elementy paska narzędzi, składniki WPF
description: Dowiedz się, jak za pomocą karty składniki WPF wyświetlić Windows Presentation Foundation kontrolki dostępne do wyboru na komputerze lokalnym.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d23418cd784b9e0b7c916c1e5629a6da012b9d0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836400"
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybieranie elementów przybornika, składniki WPF

Na tej karcie okna dialogowego **Wybieranie elementów przybornika** zostanie wyświetlona lista kontrolek Windows Presentation Foundation (WPF) dostępnych na komputerze lokalnym. Aby wyświetlić tę listę, wybierz opcję **Wybierz elementy przybornika** z menu **Narzędzia** , aby wyświetlić okno dialogowe **Wybierz elementy przybornika** , a następnie wybierz kartę **składniki WPF** . Aby posortować składniki, zaznacz dowolny nagłówek kolumny.

- Po wybraniu pola wyboru obok składnika zostanie wyświetlona ikona tego składnika w **przyborniku**.

    > [!TIP]
    > Aby dodać formant WPF do dokumentu projektu, który jest otwarty do edycji, przeciągnij jego ikonę **przybornika** na powierzchnię widok Projekt. Domyślne znaczniki i kod dla składnika są wstawiane do projektu, gotowe do modyfikacji. Aby uzyskać więcej informacji, zobacz [Przybornik](../../ide/reference/toolbox.md).

- Gdy pole wyboru obok składnika jest wyczyszczone, odpowiadająca ikona zostanie usunięta z **przybornika**.

    > [!NOTE]
    > Składniki platformy .NET zainstalowane na komputerze pozostają dostępne niezależnie od tego, czy ikony dla nich są wyświetlane w **przyborniku**.

Kolumny na karcie **składniki WPF** zawierają następujące informacje:

**Nazwa**

Wyświetla listę nazw formantów WPF, dla których wpisy istnieją w rejestrze komputera.

**Przestrzeń nazw**

Wyświetla hierarchię przestrzeni nazw [interfejsu API platformy .NET](/dotnet/api/?view=netframework-4.7&preserve-view=true) , która definiuje strukturę składnika. Sortuj według tej kolumny, aby wyświetlić listę składników dostępnych w ramach każdej przestrzeni nazw platformy .NET zainstalowanej na komputerze.

**Nazwa zestawu**

Wyświetla nazwę zestawu .NET, który zawiera przestrzeń nazw dla każdego składnika. Sortuj według tej kolumny, aby wyświetlić listę przestrzeni nazw zawartych w każdym zestawie .NET zainstalowanym na komputerze.

**Katalog**

Wyświetla lokalizację zestawu .NET. Domyślną lokalizacją dla wszystkich zestawów jest globalna pamięć podręczna zestawów. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej zestawów, zobacz [Work with assemblys and The Global Assembly Cache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista elementów UI

### <a name="filter"></a>Filtr

Filtruje listę formantów WPF na podstawie ciągu podanym w polu tekstowym. Wyświetlane są wszystkie dopasowania z jednej z czterech kolumn.

**Czyste**

Czyści ciąg filtru.

**Przeglądaj**

Otwiera okno dialogowe **otwieranie** , które umożliwia przejście do zestawów, które zawierają kontrolki WPF. Użyj tego do ładowania zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.

**Język**

Pokazuje zlokalizowany język zestawu, który zawiera wybraną kontrolkę WPF.

## <a name="limitations"></a>Ograniczenia

Dodawanie kontrolki niestandardowej lub <xref:System.Windows.Controls.UserControl> przybornika ma następujące ograniczenia:

- Działa tylko w przypadku kontrolek niestandardowych zdefiniowanych poza bieżącym projektem.

- Usługa nie jest aktualizowana prawidłowo w przypadku zmiany konfiguracji rozwiązania z debugowania na wydanie lub z wersji do debugowania. Wynika to z faktu, że odwołanie nie jest odwołaniem do projektu, ale jest przeznaczone dla zestawu na dysku. Jeśli formant jest częścią bieżącego rozwiązania, w przypadku zmiany z debugowania na wydanie, projekt nadal odwołuje się do wersji debugowania formantu.

Ponadto, jeśli metadane czasu projektowania są stosowane do kontrolki niestandardowej, a metadane określają, że dla [Microsoft. Windows. Design. ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) jest ustawiona wartość `false` , formant nie jest wyświetlany w przyborniku.

Możesz odwoływać się do kontrolek bezpośrednio w widoku XAML, mapując przestrzeń nazw i zestaw dla kontrolki.

## <a name="see-also"></a>Zobacz też

- [Przybornik](../../ide/reference/toolbox.md)
- [Rozpoczynanie pracy z aparatem WPF](../../designers/getting-started-with-wpf.md)
