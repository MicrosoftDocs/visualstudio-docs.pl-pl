---
title: Akcje kompilacji
description: W tym artykule opisano różne akcje kompilacji, które mogą być używane C# w projektach
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 97cabcacf276c6972a717e968656430ad32e37e3
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715852"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie Visual Studio dla komputerów Mac mają akcję kompilacji. Kontroluje to, co się dzieje z plikiem podczas kompilacji. To zachowanie można ustawić, klikając prawym przyciskiem myszy dowolny plik i przechodząc do **akcji kompilacji**, jak pokazano poniżej:

![Wybieranie akcji Kompiluj kompilację z Eksploratora rozwiązań](media/projects-and-solutions-image1.png)

Niektóre typowe akcje kompilacji dla C# projektów są następujące:

* **Brak** — plik nie jest częścią kompilacji w żaden sposób — jest zawarty w projekcie w celu łatwego dostępu do środowiska IDE.
* **Kompiluj** — plik zostanie przesłany do C# kompilatora jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przesłany do C# kompilatora jako zasób, który ma zostać osadzony w zestawie. [Zestawu. GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream)z przestrzeni nazw `System.Reflection` można następnie użyć do odczytania pliku z zestawu.
* **Zawartość** — w przypadku projektów ASP.NET te pliki zostaną dołączone jako część lokacji podczas jej wdrażania. W przypadku projektów Xamarin. iOS i Xamarin. Mac zostaną one uwzględnione w zbiorze aplikacji.

Istnieje możliwość wybrania więcej niż jednego pliku w Eksploratorze rozwiązań, co pozwala ustawić akcję kompilacji na wiele plików jednocześnie.

Istnieją także akcje kompilacji dla określonych projektów. Projekty Xamarin. iOS mają akcję kompilacji **BundleResource** , która spowoduje dodanie pliku jako części zbioru aplikacji. Informacje o określonych akcjach kompilacji platformy Xamarin. Android można znaleźć w przewodniku [procesu kompilacji](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) .

## <a name="see-also"></a>Zobacz także

- [Akcje kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/build-actions)