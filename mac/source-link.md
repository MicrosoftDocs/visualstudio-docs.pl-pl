---
title: Debugowanie do pakietów NuGet z łączem źródłowym
description: W tym artykule opisano funkcję łącze źródłowe w programie Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451490"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debugowanie do pakietów NuGet z łączem źródłowym

Technologia Source Link umożliwia debugowanie kodu źródłowego zestawów .NET z usługi NuGet tego statku. PdB z łączami do plików źródłowych. Source Link jest wykonywany, gdy deweloperzy tworzą pakiet NuGet i osadzają metadane kontroli źródła wewnątrz zestawów i pakietu. Gdy łącze źródłowe jest włączone w programie Visual Studio dla komputerów Mac, IDE wykryje, czy pliki źródłowe są dostępne dla zainstalowanych pakietów. Visual Studio dla komputerów Mac zaoferuje je pobrać, co pozwoli ci przejść przez kod pakietu. Source Link współpracuje również z kodem biblioteki klasy podstawowej mono dla projektów platformy Xamarin, co pozwala na przejście do kodu .NET Framework, jak również. Source Link udostępnia metadane kontroli źródła, aby utworzyć doskonałe środowisko debugowania.

> [!NOTE]
> Visual Studio dla komputerów Mac obecnie nie obsługuje serwerów symboli. Z tego powodu łącze źródłowe z metadanymi hostowanymi na serwerach symboli nie jest obsługiwane.

## <a name="enable-source-link"></a>Włącz łącze źródłowe

Aby włączyć łącze źródłowe w programie Visual Studio dla komputerów Mac, przejdź do **programu Visual Studio > preferencje... > projekty > debugera** i upewnij się, że pole wyboru Krok do kodu **zewnętrznego** jest zaznaczone.

![Zrzut ekranu przedstawiający okno dialogowe preferencji z polem wyboru Krok do kodu zewnętrznego](media/source-link1.png)

Ustawienie pobierz kod **zewnętrzny** można zmienić zgodnie z preferencjami:
* Zapytaj: Program Visual Studio dla komputerów Mac wyświetli monit o pobranie kodu zewnętrznego
* Zawsze: Visual Studio dla komputerów Mac automatycznie pobierze kod zewnętrzny
* Nigdy: Program Visual Studio dla komputerów Mac nie pobierze powiązanego kodu zewnętrznego

Domyślnie wybrano **opcję Ask.** Otrzymasz następujący monit, gdy zostanie znaleziony kod zewnętrzny dla pakietu NuGet:

![Zrzut ekranu przedstawiający monit wyświetlany po znalezieniu kodu zewnętrznego dla pakietu NuGet](media/source-link2.png)


## <a name="see-also"></a>Zobacz też

- [Repozytorium Link źródłowy GitHub](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Dokumentacja platformy .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) dotycząca łącza źródłowego i więcej informacji na temat dodawania obsługi łącza źródłowego do pakietów
