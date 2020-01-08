---
title: Debugowanie do pakietów NuGet za pomocą linku źródłowego
description: W tym artykule opisano funkcję linku źródłowego w Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451490"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debugowanie do pakietów NuGet za pomocą linku źródłowego

Technologia linku źródłowego umożliwia debugowanie kodu źródłowego zestawów .NET z pakietu NuGet, który jest dostarczany. Plików PDB z linkami do plików źródłowych. Łącze źródłowe jest wykonywane, gdy deweloperzy tworzą pakiet NuGet i osadzają metadane kontroli źródła wewnątrz zestawów i pakietów. Gdy link źródłowy jest włączony w Visual Studio dla komputerów Mac, IDE wykryje, czy pliki źródłowe są dostępne dla zainstalowanych pakietów. Następnie Visual Studio dla komputerów Mac będzie oferować pobieranie, co umożliwi przechodzenie przez kod pakietu. Link źródłowy współdziała również z kodem biblioteki klas bazowych mono dla projektów platformy Xamarin, co pozwala na przechodzenie do .NET Framework kodzie. Link źródłowy udostępnia metadane kontroli źródła w celu utworzenia doskonałego środowiska debugowania.

> [!NOTE]
> Visual Studio dla komputerów Mac obecnie nie obsługuje serwerów symboli. Z tego powodu link źródłowy z metadanymi hostowanymi na serwerach symboli nie jest obsługiwany.

## <a name="enable-source-link"></a>Włącz link źródłowy

Aby włączyć link źródłowy w Visual Studio dla komputerów Mac, przejdź do **preferencji > programu Visual Studio... > Projekty > debuger** i upewnij się, że jest zaznaczone pole wyboru **Wkrocz do kodu zewnętrznego** .

![Zrzut ekranu okna dialogowego preferencji pokazujący krok do kodu zewnętrznego](media/source-link1.png)

Możesz zmienić ustawienie w polu **Pobierz kod zewnętrzny** , aby dopasować preferencje:
* Pytaj: Visual Studio dla komputerów Mac wyświetli monit o pobranie kodu zewnętrznego
* Zawsze: Visual Studio dla komputerów Mac automatycznie pobierze kod zewnętrzny
* Nigdy: Visual Studio dla komputerów Mac nie pobiera pokrewnego kodu zewnętrznego

Domyślnie jest zaznaczone polecenie **zadawaj** . Po znalezieniu kodu zewnętrznego dla pakietu NuGet zostanie wyświetlony następujący monit:

![Zrzut ekranu przedstawiający monit wyświetlany po znalezieniu zewnętrznego kodu dla pakietu NuGet](media/source-link2.png)


## <a name="see-also"></a>Zobacz także

- [Repozytorium usługi GitHub linku źródłowego](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Dokumentacja platformy .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) dotycząca linku źródłowego i więcej informacji na temat dodawania obsługi linków źródłowych do pakietów
