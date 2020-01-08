---
title: 'Projektant przepływu pracy: System. Activities, wybierz elementy przybornika'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f1a7030b6c351407814314ccd41e0e2ed6a880e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593112"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Karta System. Activities, okno dialogowe Wybieranie elementów przybornika

Na tej karcie okna dialogowego **Wybieranie elementów przybornika** zostanie wyświetlona lista działań, szablonów i elementów Windows Workflow Foundation (WF), które są dostępne dla użytkownika. Aby wyświetlić tę listę, zaznacz opcję **Wybierz elementy przybornika** z menu **Narzędzia** lub klikając prawym przyciskiem myszy **Przybornik** i wybierając **pozycję Wybierz elementy** , aby wyświetlić okno dialogowe **Wybieranie elementów przybornika** , a następnie wybierz jego kartę **System. działania** . poza tym lista zawiera działania przepływu pracy z zestawów System. Activities, system. ServiceModel. Activities i system. Activities. Core. Presentation. Jednak są domyślnie zaznaczone tylko działania dostarczone przez system oraz działania dodane za pomocą innych zestawów wyświetlanych w **przyborniku** . Ostatnio dodane działania są automatycznie sprawdzane i pojawiają się w **przyborniku** po kliknięciu przycisku **OK** w oknie dialogowym. Te elementy są również wyświetlane w **przyborniku** pod nową kategorią, która odnosi się do przestrzeni nazw, w której znajduje się działanie/element/szablon.

> [!WARNING]
> Jeśli spróbujesz dodać zestaw, który nie zawiera żadnych działań przepływu pracy, zostanie wyświetlone okno dialogowe błędu z wyjaśnieniem, że zestaw nie zawiera żadnych działań.

To okno dialogowe jest niezależny od Project, a tym samym w przypadku, gdy karta **System. Activities** będzie nadal wyświetlana w AUTONOMICZNYM języku XAML lub typie projektu innego niż przepływ pracy.

Filtrowanie odbywa się na każdej karcie i nie jest możliwe dodawanie działań przepływu pracy za pomocą karty **składnik platformy .NET** . Dodaj je za pomocą samej karty **System. Activities** .

Możesz usunąć zaznaczenie wszystkich elementów, które nie mają być wyświetlane w **przyborniku** z tej karty okna dialogowego, lub alternatywnie, możesz użyć opcji **Usuń** kliknięcie prawym przyciskiem myszy w **przyborniku** , a cofnięcie odwołania do zestawu nie powoduje usunięcia elementu z **przybornika**.

Tworzenie wystąpienia działania przez przeciąganie i upuszczanie go w projektancie dodaje zestaw, który zawiera element do listy przywoływanych zestawów. Ponadto, jeśli działanie odwołuje się do zestawu C, nie dodaje C do listy zestawów, do których się odwołuje. Zestaw C musi znajdować się w pamięci podręcznej GAC lub w tym samym katalogu, w którym działa B. W przypadku autonomicznego zestaw musi znajdować się w pamięci podręcznej lub w ścieżkach sondy programu VS. Tylko wtedy można przeciągnąć i upuścić działanie na powierzchni projektanta przepływu pracy.

Ustawienia **przybornika** są zapisywane domyślnie jako opcje użytkownika, więc przy następnym otwarciu **przybornika**zostanie wyświetlona dostosowana lista działań przepływu pracy. Jednym z efektów ubocznych tego jest to, że jeśli dodano określone elementy domeny do **przybornika** za pomocą okna dialogowego **Wybierz elementy przybornika** , nadal będą widoczne te elementy, gdy pracujesz również w aplikacji konsolowej przepływu pracy. Jeśli nie chcesz ich zobaczyć, usuń je za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy lub usuń zaznaczenie tych pól w oknie dialogowym **Wybierz elementy przybornika** , tak jak zostało to opisane wcześniej.

Kolumny w tym oknie dialogowym zawierają następujące informacje:

Nazwij
Wyświetla listę nazw działań przepływu pracy aktualnie zarejestrowanych na komputerze lokalnym.

Obszaru
Wyświetla hierarchię przestrzeni nazw .NET, która definiuje strukturę działania.

Name zestawu\
Wyświetla nazwę i wersję zestawu .NET zawierającego działanie.

Katalogi
Wyświetla lokalizację zestawu .NET zawierającego działania przepływu pracy. Domyślną lokalizacją dla wszystkich zestawów jest globalna pamięć podręczna zestawów.

Aby posortować składniki, zaznacz dowolny nagłówek kolumny.
