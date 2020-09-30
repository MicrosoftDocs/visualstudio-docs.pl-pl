---
title: Debugowanie do pakietów NuGet za pomocą linku źródłowego
description: W tym artykule opisano funkcję linku źródłowego w Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583921"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debugowanie do pakietów NuGet za pomocą linku źródłowego

Technologia linku źródłowego umożliwia debugowanie kodu źródłowego zestawów .NET z pakietu NuGet, który jest dostarczany. Plików PDB z linkami do plików źródłowych. Łącze źródłowe jest wykonywane, gdy deweloperzy tworzą pakiet NuGet i osadzają metadane kontroli źródła wewnątrz zestawów i pakietów. Gdy link źródłowy jest włączony w Visual Studio dla komputerów Mac, IDE wykryje, czy pliki źródłowe są dostępne dla zainstalowanych pakietów. Następnie Visual Studio dla komputerów Mac będzie oferować pobieranie, co umożliwi przechodzenie przez kod pakietu. Link źródłowy współdziała również z kodem biblioteki klas bazowych mono dla projektów platformy Xamarin, co pozwala na przechodzenie do .NET Framework kodzie. Link źródłowy udostępnia metadane kontroli źródła w celu utworzenia doskonałego środowiska debugowania.

> [!NOTE]
> Visual Studio dla komputerów Mac obecnie nie obsługuje serwerów symboli. Z tego powodu link źródłowy z metadanymi hostowanymi na serwerach symboli nie jest obsługiwany.

## <a name="enable-source-link"></a>Włącz link źródłowy

Aby włączyć link źródłowy w Visual Studio dla komputerów Mac, przejdź do sekcji **preferencje > programu Visual Studio... > projekty > debuger** i upewnij się, że jest zaznaczone pole wyboru **Wkrocz do kodu zewnętrznego** .

![Zrzut ekranu okna dialogowego preferencji pokazujący krok do kodu zewnętrznego](media/source-link1.png)

Możesz zmienić ustawienie w polu **Pobierz kod zewnętrzny** , aby dopasować preferencje:
* Pytaj: Visual Studio dla komputerów Mac wyświetli monit o pobranie kodu zewnętrznego
* Zawsze: Visual Studio dla komputerów Mac automatycznie pobierze kod zewnętrzny
* Nigdy: Visual Studio dla komputerów Mac nie pobiera pokrewnego kodu zewnętrznego

Domyślnie jest zaznaczone polecenie **zadawaj** . Po znalezieniu kodu zewnętrznego dla pakietu NuGet zostanie wyświetlony następujący monit:

![Zrzut ekranu przedstawiający monit wyświetlany po znalezieniu zewnętrznego kodu dla pakietu NuGet](media/source-link2.png)


## <a name="see-also"></a>Zobacz też

- [Repozytorium usługi GitHub linku źródłowego](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Dokumentacja platformy .NET](/dotnet/standard/library-guidance/sourcelink) dotycząca linku źródłowego i więcej informacji na temat dodawania obsługi linków źródłowych do pakietów