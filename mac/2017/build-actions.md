---
title: Akcje kompilacji
description: W tym artykule opisano różne akcje kompilacji, które mogą być używane dla projektów języka C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983250"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w projekcie programu Visual Studio dla komputerów Mac mają akcję kompilacji. Kontroluje, co dzieje się z plikiem podczas kompilacji. To zachowanie można ustawić, klikając prawym przyciskiem myszy dowolny plik i przeglądając **polecenie Build Action**, jak pokazano poniżej:

![Wybieranie akcji kompilacji kompilacji kompilacji kompilacji z Eksploratora rozwiązań](media/projects-and-solutions-image1.png)

Niektóre z typowych akcji kompilacji dla projektów języka C#:

* **Brak** — plik nie jest częścią kompilacji w żaden sposób — jest zawarty w projekcie w celu łatwego dostępu z IDE.
* **Compile** — plik zostanie przekazany do kompilatora języka C# jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przekazany do kompilatora języka C# jako zasób, który ma być osadzony w zestawie. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` z obszaru nazw, może następnie służyć do odczytu pliku z zestawu.
* **Zawartość** — w przypadku projektów ASP.NET pliki te zostaną uwzględnione jako część witryny po jej wdrożeniu. W przypadku projektów xamarin.iOS i Xamarin.Mac zostaną one uwzględnione w pakiecie aplikacji.

Istnieje możliwość wybrania więcej niż jednego pliku w Eksploratorze rozwiązań, co pozwala ustawić akcję kompilacji na wiele plików jednocześnie.

Ponadto istnieją działania kompilacji dla określonych projektów. Xamarin.iOS projekty mają **BundleResource** akcji kompilacji, która doda plik jako część pakietu aplikacji. Informacje na temat akcji kompilacji specyficzne dla systemu Xamarin.Android można znaleźć w przewodniku [po procesie kompilacji.](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)

## <a name="see-also"></a>Zobacz też

- [Akcje kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/build-actions)