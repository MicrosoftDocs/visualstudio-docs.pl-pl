---
title: 'Rozwiązywanie problemów: Jak mogę wydać nową wersję mojego istniejącego rozszerzenia?'
description: Przewodnik dotyczący aktualizowania istniejących rozszerzeń za pośrednictwem przepływu pracy publikowania.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488466"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Rozwiązywanie problemów: Jak mogę wydać nową wersję mojego istniejącego rozszerzenia?

> [!IMPORTANT]
> Obecnie tworzenie nowych rozszerzeń nie jest oficjalnie obsługiwane w programie Visual Studio 2019 for Mac.

Serwer repozytorium rozszerzeń Visual Studio dla komputerów Mac zostanie przenoszony 15 stycznia 2021. Przeniesienie nie będzie miało wpływu na użytkowników, którzy już pobrali Twoje rozszerzenie, ale zmienią sposób publikowania nowych wersji rozszerzenia po tej dacie.

Jako autor istniejącego rozszerzenia musisz użyć innego przepływu pracy, aby zwolnić dalsze aktualizacje. Ten proces składa się z:
- Konfigurowanie publicznego repozytorium GitHub dla każdego rozszerzenia
- Udostępnianie adresu URL repozytorium do zespołu Visual Studio dla komputerów Mac za pośrednictwem [listy adresowej publikowania rozszerzeń](mailto:vsmextpub@microsoft.com)
- Aktualizowanie rozszerzenia przy użyciu funkcji releases w serwisie GitHub


## <a name="initial-setup"></a>Początkowa konfiguracja 

Aby kontynuować publikowanie aktualizacji rozszerzeń, należy utworzyć publiczne repozytorium GitHub. W przypadku publikowania wielu rozszerzeń należy mieć oddzielne repozytorium dla każdego z nich, chyba że jest to zawsze wersja i publikacja razem, w takim przypadku można użyć jednego repozytorium.

> [!NOTE]
> Mimo że repozytorium GitHub dla swojego rozszerzenia musi być publiczne, nie musisz hostować żadnego kodu w tym miejscu. Następujący proces nie wymaga posiadania żadnego kodu w usłudze GitHub.


## <a name="share-the-location-of-your-repository"></a>Udostępnianie lokalizacji repozytorium

Po skonfigurowaniu repozytorium Wyślij wiadomość e-mail do [listy adresowej publikowania rozszerzenia](mailto:vsmextpub@microsoft.com) przy użyciu adresu URL.


## <a name="release-a-new-version"></a>Zwolnij nową wersję

Użyjesz linku "Utwórz nowe wydanie" na stronie głównej repozytorium, aby rozpocząć proces aktualizowania rozszerzenia. Po wybraniu tego linku wykonaj następujące kroki:

1. Dodaj informacje do **wersji tagu** wydania w następującym formacie

    > \<releaseVersion> \- VSM v\<targetVersion>

    Gdzie:
     - **&lt; releaseVersion &gt;** jest numerem wersji rozszerzenia
     - **&lt; targetVersion &gt;** jest minimalną wersją Visual Studio dla komputerów Mac Twoje rozszerzenie jest ukierunkowane

2. Obowiązkowe Pola **tytuł** i **Opis** mogą być wypełniane wszystkimi dowolnymi informacjami. Ten przepływ pracy nie używa informacji z tych pól.

3. Upewnij się **, że** pole wyboru nie jest zaznaczone. Jeśli ta opcja jest zaznaczona, wydanie nie zostanie pobrane przez ten proces publikowania.

4. Dołącz pliki **. Mpack** , które implementują rozszerzenie w sekcji **plików binarnych** . Możliwe jest dołączenie wielu plików **. Mpack** w wersji.

W Visual Studio dla komputerów Mac zostanie wyświetlona Najnowsza wersja rozszerzenia, która jest zgodna z instalacją Visual Studio dla komputerów Mac, która została użyta w celu uzyskania dostępu do repozytorium rozszerzeń.

Dopóki Twoje repozytorium GitHub zostało zarejestrowane za pomocą zespołu Visual Studio dla komputerów Mac, wydanie rozszerzenia zostanie pobrane przez Visual Studio dla komputerów Mac w ciągu 24 godzin.

## <a name="additional-information"></a>Dodatkowe informacje

- Wersje, które nie są zgodne z powyższymi wymaganiami, nie zostaną opublikowane. 
- Po 15 stycznia 2021 aktualizacje rozszerzeń będą wyświetlane tylko w Visual Studio dla komputerów Mac 8,0 lub nowszym.
- Istniejące rozszerzenia pozostaną dostępne do Visual Studio dla komputerów Mac użytkownikom bez żadnej akcji. Należy postępować zgodnie z instrukcjami w tym przewodniku w przypadku opublikowania nowej wersji po 15 stycznia 2021.
