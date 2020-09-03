---
title: Akcje kompilacji
description: W tym artykule opisano różne akcje kompilacji, które mogą być używane dla projektów C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74983250"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie Visual Studio dla komputerów Mac mają akcję kompilacji. Kontroluje to, co się dzieje z plikiem podczas kompilacji. To zachowanie można ustawić, klikając prawym przyciskiem myszy dowolny plik i przechodząc do **akcji kompilacji**, jak pokazano poniżej:

![Wybieranie akcji Kompiluj kompilację z Eksploratora rozwiązań](media/projects-and-solutions-image1.png)

Niektóre typowe akcje kompilacji dla projektów C# to:

* **Brak** — plik nie jest częścią kompilacji w żaden sposób — jest zawarty w projekcie w celu łatwego dostępu do środowiska IDE.
* **Kompiluj** — plik zostanie przesłany do kompilatora C# jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przesłany do kompilatora C# jako zasób, który ma zostać osadzony w zestawie. [Zestawu. GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream)z `System.Reflection` przestrzeni nazw można następnie użyć do odczytania pliku z zestawu.
* **Zawartość** — w przypadku projektów ASP.NET te pliki zostaną dołączone jako część lokacji podczas jej wdrażania. W przypadku projektów Xamarin. iOS i Xamarin. Mac zostaną one uwzględnione w zbiorze aplikacji.

Istnieje możliwość wybrania więcej niż jednego pliku w Eksploratorze rozwiązań, co pozwala ustawić akcję kompilacji na wiele plików jednocześnie.

Istnieją także akcje kompilacji dla określonych projektów. Projekty Xamarin. iOS mają akcję kompilacji **BundleResource** , która spowoduje dodanie pliku jako części zbioru aplikacji. Informacje o określonych akcjach kompilacji platformy Xamarin. Android można znaleźć w przewodniku [procesu kompilacji](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) .

## <a name="see-also"></a>Zobacz też

- [Akcje kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/build-actions)