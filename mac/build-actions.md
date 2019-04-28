---
title: Akcje kompilacji
description: W tym artykule opisano różne akcje kompilacji, których można użyć dla projektów C#
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 16617f8de15fbef40941c4f9409497da142c9e8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62983421"
---
# <a name="build-actions"></a>Akcje kompilacji

Wszystkie pliki w programie Visual Studio dla komputerów Mac projektu mają akcji kompilacji. Kontroluje, co się dzieje z pliku podczas kompilacji. To zachowanie można ustawić, klikając prawym przyciskiem myszy dowolny plik i przechodząc do **Build Action**, jak pokazano poniżej:

![Wybieranie akcji kompilacji w kompilacji za pomocą Eksploratora rozwiązań](media/projects-and-solutions-image1.png)

Akcje niektóre typowe kompilacji dla projektów języka C#:

* **Brak** — plik nie jest częścią kompilacji w jakikolwiek sposób — znajduje się w projekcie, aby mieć łatwy dostęp z poziomu środowiska IDE.
* **Skompilować** — plik zostanie przekazany do kompilatora C# jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przekazany do kompilatora C# jako zasób do osadzenia w zestawie. [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream), z `System.Reflection` przestrzeni nazw, można odczytać pliku z zestawu.
* **Zawartość** — dla projektów platformy ASP.NET, te pliki będą dołączane jako część lokacji podczas jej wdrażania. Projekty Xamarin.iOS i Xamarin.Mac zostaną one uwzględnione w zbiorze aplikacji.

Użytkownik może wybrać więcej niż jeden plik w Eksploratorze rozwiązań, co pozwala ustawić akcji kompilacji do wielu plików jednocześnie.

Ponadto istnieją akcje kompilacji dla konkretnych projektów. Projekty Xamarin.iOS mają **BundleResource** tworzenie akcji, która doda go jako część pakietu aplikacji. Informacje o akcjach określonej kompilacji platformy Xamarin.Android znajdują się w [proces kompilacji](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) przewodnik.

## <a name="see-also"></a>Zobacz także

- [Tworzenie akcji (Visual Studio Windows)](/visualstudio/ide/build-actions)