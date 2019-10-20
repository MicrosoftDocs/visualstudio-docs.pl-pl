---
title: Wybierz elementy przybornika, składniki WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c7967635d8e5d64907587fcd1a9b4d84a31d569
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660916"
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybierz elementy paska narzędzi, składniki WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na tej karcie okna dialogowego **Wybieranie elementów przybornika** zostanie wyświetlona lista kontrolek Windows Presentation Foundation (WPF) dostępnych na komputerze lokalnym. Aby wyświetlić tę listę, wybierz opcję **Wybierz elementy przybornika** z menu **Narzędzia** , aby wyświetlić okno dialogowe **Wybierz elementy przybornika** , a następnie wybierz kartę **składniki WPF** . Aby posortować składniki, zaznacz dowolny nagłówek kolumny.

- Po wybraniu pola wyboru obok składnika zostanie wyświetlona ikona tego składnika w **przyborniku**.

  > [!TIP]
  > Aby dodać wystąpienie formantu WPF do dokumentu projektu otwartego do edycji, przeciągnij jego ikonę **przybornika** na powierzchnię widok Projekt. Domyślne znaczniki i kod dla składnika są wstawiane do projektu, gotowe do modyfikacji. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie oknem przybornika](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) i [instrukcje: manipulowanie kartami przybornika](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Gdy pole wyboru obok składnika jest wyczyszczone, odpowiednia ikona zostanie usunięta z **przybornika.**

  > [!NOTE]
  > Składniki .NET Framework zainstalowane na komputerze pozostają dostępne niezależnie od tego, czy ikony dla nich są wyświetlane w **przyborniku**.

  Kolumny na karcie **składniki WPF** zawierają następujące informacje:

  Nazwa wyświetla listę nazw formantów WPF, dla których wpisy istnieją w rejestrze komputera.

  Przestrzeń nazw Wyświetla hierarchię przestrzeni nazw [NIB: .NET Framework Library](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) , która definiuje strukturę składnika. Sortuj według tej kolumny, aby wyświetlić listę składników dostępnych w ramach poszczególnych przestrzeni nazw .NET Framework zainstalowanych na komputerze.

  Nazwa zestawu zawiera nazwę zestawu .NET Framework zawierającego przestrzeń nazw dla każdego składnika. Sortuj według tej kolumny, aby wyświetlić listę przestrzeni nazw zawartych w poszczególnych zestawach .NET Framework zainstalowanych na komputerze.

  Katalog zawiera lokalizację zestawu .NET Framework. Domyślną lokalizacją dla wszystkich zestawów jest globalna pamięć podręczna zestawów. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej zestawów, zobacz [Praca z zestawami i globalną pamięcią podręczną zestawów](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>Lista elementów UI
 **Filtr** Filtruje listę formantów WPF na podstawie ciągu podanym w polu tekstowym. Wyświetlane są wszystkie dopasowania z jednej z czterech kolumn.

 **Wyczyść** Czyści ciąg filtru.

 **Przeglądaj** Otwiera okno dialogowe **otwieranie** , które umożliwia przejście do zestawów, które zawierają kontrolki WPF. Użyj tego do ładowania zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.

 **Język** Pokazuje zlokalizowany język zestawu, który zawiera wybraną kontrolkę WPF.

## <a name="limitations"></a>Ograniczenia
 Dodawanie kontrolki niestandardowej lub <xref:System.Windows.Controls.UserControl> do przybornika ma następujące ograniczenia.

- Działa tylko w przypadku kontrolek niestandardowych zdefiniowanych poza bieżącym projektem.

- Usługa nie jest aktualizowana prawidłowo w przypadku zmiany konfiguracji rozwiązania z debugowania na wydanie lub z wersji do debugowania. Wynika to z faktu, że odwołanie nie jest odwołaniem do projektu, ale jest przeznaczone dla zestawu na dysku. Jeśli formant jest częścią bieżącego rozwiązania, w przypadku zmiany z debugowania na wydanie, projekt nadal odwołuje się do wersji debugowania formantu.

  Ponadto, jeśli metadane czasu projektowania są stosowane do kontrolki niestandardowej, a metadane określają, że [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) jest ustawiony na `false`, formant nie jest wyświetlany w przyborniku.

  Możesz odwoływać się do kontrolek bezpośrednio w widoku XAML, mapując przestrzeń nazw i zestaw dla kontrolki. Aby uzyskać więcej informacji, zobacz [jak: importowanie przestrzeni nazw do XAML](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Zobacz także

- [Okno dialogowe Wybieranie elementów przybornika (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Przybornik](../../ide/reference/toolbox.md)
- [Instrukcje: korzystanie z kontrolki WPF innej firmy w aplikacji WPF](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [Projektant WPF](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)