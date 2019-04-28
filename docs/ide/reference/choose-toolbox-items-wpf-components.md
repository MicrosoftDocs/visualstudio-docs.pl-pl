---
title: Wybierz elementy paska narzędzi, składniki WPF
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09afb11708afb310a3dcd52490f5b2bcda9d79b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790931"
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybierz elementy paska narzędzi, składniki WPF

Ta karta **wybierz elementy przybornika** okno dialogowe wyświetla listę formantów Windows Presentation Foundation (WPF), które są dostępne na komputerze lokalnym. Do wyświetlania tej listy, wybierz **wybierz elementy przybornika** z **narzędzia** menu, aby wyświetlić **wybierz elementy przybornika** okno dialogowe, a następnie wybierz jego **WPF Składniki** kartę. Aby posortować składniki na liście, wybierz nagłówek dowolnej kolumny.

- Gdy zaznaczone jest pole wyboru obok składnika, ikona tych składników, będą wyświetlane w **przybornika**.

    > [!TIP]
    > Aby dodać kontrolki WPF do dokumentu zawierającego projekt jest otwarty do edycji, przeciągnij jego **przybornika** ikony na powierzchnię projektową widoku. Domyślne znaczników i kodu dla składnika są wstawiane do projektu, możesz zmodyfikować. Aby uzyskać więcej informacji, zobacz [przybornika](../../ide/reference/toolbox.md).

- Po wyczyszczeniu pola wyboru obok składnika odpowiednią ikonę zostaną usunięte z **przybornika**.

    > [!NOTE]
    > Składniki .NET Framework zainstalowana na danym komputerze pozostaną dostępne, czy ich ikony są wyświetlane w **przybornika**.

Kolumny na **składniki WPF** karta zawiera następujące informacje:

**Nazwa**

Wyświetla listę nazw kontrolek WPF, dla których wpisy znajdują się w rejestrze na komputerze.

**Namespace**

Wyświetla hierarchię [interfejsu API programu .NET Framework klasy](/dotnet/api/?view=netframework-4.7) przestrzeni nazw, który definiuje strukturę składnika. Sortuj w tej kolumnie, aby wyświetlić listę dostępnych składników w każdej przestrzeni nazw z .NET Framework zainstalowana na danym komputerze.

**Nazwa zestawu**

Wyświetla nazwę zestawu .NET Framework, który zawiera przestrzeń nazw dla każdego składnika. Sortuj od tej kolumny, aby wyświetlić listę przestrzeni nazw zawartych w każdym zestawie .NET Framework zainstalowana na danym komputerze.

**Directory**

Wyświetla lokalizację zestawu .NET Framework. Domyślna lokalizacja dla wszystkich zestawów to Global Assembly Cache. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej zestawów, zobacz [Praca z zestawami i Global Assembly Cache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista elementów UI

### <a name="filter"></a>Filtr

Filtruje listę kontrolek WPF, w oparciu o ciąg, który należy podać w polu tekstowym. Wyświetlane są wszystkie dopasowania z dowolnego z czterech kolumn.

**Usuń zaznaczenie**

Czyści ciągu filtru.

**Przeglądaj**

Otwiera **Otwórz** okno dialogowe, które umożliwia przejście do zespołów, które zawierają formanty WPF. Umożliwia ładowanie zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.

**Język**

Pokazuje zlokalizowanego języka zestawu, który zawiera wybranej kontrolki WPF.

## <a name="limitations"></a>Ograniczenia

Dodawanie niestandardowego formantu lub <xref:System.Windows.Controls.UserControl> do przybornika ma następujące ograniczenia:

- Działa tylko w przypadku kontrolek niestandardowych, zdefiniowanych poza bieżącym projekcie.

- Nie jest aktualizowany poprawnie po zmianie konfiguracji rozwiązania z debugowania na wydanie lub wersja do debugowania. Jest to spowodowane odwołania nie jest odwołanie do projektu, ale zamiast tego jest dla zestawu na dysku. Jeśli kontrolka jest częścią bieżącego rozwiązania, gdy zmienią się z poziomu pozycji Debuguj wydania, projekt w dalszym ciągu odwoływać się do kontroli wersji do debugowania.

Ponadto, jeśli metadanych w czasie projektowania jest stosowany do formantu niestandardowego i metadane Określa, że <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> ustawiono `false`, formant nie jest wyświetlana w przyborniku.

Możesz odwoływać się kontrolkom bezpośrednio w widoku XAML przez mapowanie przestrzeni nazw i zestawu dla formantu.

## <a name="see-also"></a>Zobacz także

- [Przybornik](../../ide/reference/toolbox.md)
- [Wprowadzenie do korzystania z platformy WPF](../../designers/getting-started-with-wpf.md)
