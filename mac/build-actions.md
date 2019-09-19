---
title: Akcje kompilacji
description: W tym artykule opisano różne akcje kompilacji, które mogą być używane C# w projektach
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 5a0d7c6646fac83ef70fbe2aa7384dcee992d726
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128439"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie Visual Studio dla komputerów Mac mają akcję kompilacji. Akcja kompilacji kontroluje, co się dzieje z plikiem podczas kompilacji. 

>[!NOTE]
>Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows Zapoznaj się z tematem [Build Actions](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Ustawianie akcji kompilacji

Aby ustawić akcję kompilacji dla pliku w Visual Studio dla komputerów Mac, można kliknąć prawym przyciskiem myszy dowolny plik i przejść do **akcji kompilacji**, jak pokazano poniżej:

![Wybieranie akcji Kompiluj kompilację z Eksploratora rozwiązań](media/projects-and-solutions-image1.png)

Akcje kompilacji dla tego pliku zostaną wyświetlone w menu wysuwanym. 

## <a name="build-action-values"></a>Wartości akcji kompilacji

Niektóre typowe akcje kompilacji dla projektów, które można kompilować w Visual Studio dla komputerów Mac obejmują:

|Akcja kompilacji | Typy projektów | Opis |
|--|--|--|
| **Opracowania** | Ile | Plik jest przesyłany do C# kompilatora jako plik źródłowy.|
| **Zawartość** | .NET, Xamarin | W przypadku projektów ASP.NET te pliki są uwzględniane jako część lokacji podczas jej wdrażania. W przypadku projektów Xamarin. iOS i Xamarin. Mac zostaną one uwzględnione w zbiorze aplikacji.|
| **Zasób osadzony** | .NET | Plik jest przesyłany do C# kompilatora jako zasób, który ma zostać osadzony w zestawie. [Zestawu. GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream)z `System.Reflection` przestrzeni nazw można następnie użyć do odczytania pliku z zestawu.|
| **Brak** | Ile | Plik nie jest częścią kompilacji i jest dołączany do projektu w celu łatwego dostępu do środowiska IDE. Ta wartość może być używana dla plików dokumentacji, takich jak pliki Readme, na przykład.|

> [!NOTE]
> Dodatkowe akcje kompilacji mogą być definiowane przez dla określonych typów projektów, więc lista akcji kompilacji zależy od typu projektu i wartości, które nie znajdują się na liście.  

Projekty Xamarin. iOS mają akcję kompilacji **BundleResource** , która spowoduje dodanie pliku jako części zbioru aplikacji. Informacje o określonych akcjach kompilacji platformy Xamarin. Android można znaleźć w przewodniku [procesu kompilacji](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) .

Istnieje również możliwość wybrania więcej niż jednego pliku w Eksploratorze rozwiązań, co pozwala ustawić akcję kompilacji na wiele plików jednocześnie.

## <a name="see-also"></a>Zobacz także

- [Akcje kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/build-actions)