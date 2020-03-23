---
title: Akcje kompilacji
description: W tym artykule opisano różne akcje kompilacji, które mogą być używane dla projektów języka C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714405"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie programu Visual Studio dla komputerów Mac mają akcję kompilacji. Akcja kompilacji kontroluje, co dzieje się z plikiem podczas kompilacji. 

>[!NOTE]
>W tym temacie stosuje się do programu Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows zobacz [Akcje kompilacji](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Ustawianie akcji kompilacji

Aby ustawić akcję kompilacji dla pliku w programie Visual Studio dla komputerów Mac, można kliknąć prawym przyciskiem myszy dowolny plik i przeglądać do **kompilacji akcji,** jak pokazano poniżej:

![Wybieranie akcji kompilacji kompilacji kompilacji kompilacji z Eksploratora rozwiązań](media/projects-and-solutions-image1.png)

Akcje kompilacji dla tego pliku będą wyświetlane w menu wysuwanym. 

## <a name="build-action-values"></a>Tworzenie wartości akcji

Niektóre z typowych akcji kompilacji dla projektów, które można utworzyć w programie Visual Studio dla komputerów Mac obejmują:

|Akcja kompilacji | Typy projektów | Opis |
|--|--|--|
| **Skompilować** | Wszelki | Plik jest przekazywany do kompilatora języka C# jako plik źródłowy.|
| **Zawartość** | .NET, Xamarin | W przypadku projektów ASP.NET pliki te są uwzględniane jako część witryny po wdrożeniu. W przypadku projektów xamarin.iOS i Xamarin.Mac zostaną one uwzględnione w pakiecie aplikacji.|
| **Zasób osadzony** | .NET | Plik jest przekazywany do kompilatora języka C# jako zasób, który ma być osadzony w zestawie. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` z obszaru nazw, może następnie służyć do odczytu pliku z zestawu.|
| **Brak** | Wszelki | Plik nie jest częścią kompilacji w jakikolwiek sposób i jest zawarty w projekcie dla łatwego dostępu z IDE. Ta wartość może służyć do plików dokumentacji, takich jak "ReadMe" plików, na przykład.|

> [!NOTE]
> Dodatkowe akcje kompilacji mogą być definiowane przez dla określonych typów projektów, więc lista akcji kompilacji zależy od typu projektu i wartości mogą pojawić się, które nie znajdują się na tej liście.  

Xamarin.iOS projekty mają **BundleResource** akcji kompilacji, która doda plik jako część pakietu aplikacji. Informacje na temat akcji kompilacji specyficzne dla systemu Xamarin.Android można znaleźć w przewodniku [po procesie kompilacji.](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)

Istnieje również możliwość wybrania więcej niż jednego pliku w Eksploratorze rozwiązań, co pozwala ustawić akcję kompilacji na wiele plików jednocześnie.

## <a name="see-also"></a>Zobacz też

- [Akcje kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/build-actions)