---
title: Karta System. Activities, okno dialogowe Wybieranie elementów przybornika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655167"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities, karta, Wybieranie elementów przybornika, okno dialogowe
Na tej karcie okna dialogowego **Wybieranie elementów przybornika** zostanie wyświetlona lista działań [!INCLUDE[wf](../includes/wf-md.md)], szablonów i elementów, które są dostępne dla użytkownika. Aby wyświetlić tę listę, wybierz opcję **Wybierz elementy przybornika** z menu **Narzędzia** lub klikając prawym przyciskiem myszy **Przybornik** i wybierając **pozycję Wybierz elementy** , aby wyświetlić okno dialogowe **Wybierz elementy przybornika** , a następnie wybrać jego  **Karta System. Activities** . poza ramką lista zawiera działania przepływów pracy z zestawów System. Activities, system. ServiceModel. Activities i system. Activities. Core. Presentation. Jednak są domyślnie zaznaczone tylko działania dostarczone przez system oraz działania dodane za pomocą innych zestawów wyświetlanych w **przyborniku** . Ostatnio dodane działania są automatycznie sprawdzane i pojawiają się w **przyborniku** po kliknięciu przycisku **OK** w oknie dialogowym. Te elementy są również wyświetlane w **przyborniku** pod nową kategorią, która odnosi się do przestrzeni nazw, w której znajduje się działanie/element/szablon.

> [!WARNING]
> Jeśli spróbujesz dodać zestaw, który nie zawiera żadnych działań przepływu pracy, zostanie wyświetlone okno dialogowe błędu z wyjaśnieniem, że zestaw nie zawiera żadnych działań.

 To okno dialogowe jest niezależny od Project, a tym samym w przypadku, gdy karta **System. Activities** będzie nadal wyświetlana w AUTONOMICZNYM języku XAML lub typie projektu innego niż przepływ pracy.

 Filtrowanie odbywa się na każdej karcie. Oznacza to, że nie jest możliwe dodawanie działań przepływu pracy za pomocą karty **składnik platformy .NET** . Muszą one być dodawane za pomocą samej karty **System. Activities** .

 Możesz usunąć zaznaczenie wszystkich elementów, które nie mają być wyświetlane w **przyborniku** z tej karty okna dialogowego, lub alternatywnie, możesz użyć opcji menu **Usuń** kontekst w **przyborniku** , a cofnięcie odwołania do zestawu nie powoduje usunięcia elementu z  **Przybornik**.

 Tworzenie wystąpienia działania przez przeciąganie i upuszczanie go w projektancie dodaje zestaw, który zawiera element do listy przywoływanych zestawów. Ponadto, jeśli działanie odwołuje się do zestawu C, nie dodaje C do listy zestawów, do których się odwołuje. Zestaw C musi znajdować się w pamięci podręcznej GAC lub w tym samym katalogu, w którym działa B. W przypadku autonomicznego zestaw musi znajdować się w pamięci podręcznej lub w ścieżkach sondy programu VS. Tylko wtedy można przeciągnąć i upuścić działanie na powierzchni projektanta przepływu pracy.

 Ustawienia **przybornika** są zapisywane domyślnie jako opcje użytkownika, więc przy następnym otwarciu **przybornika**zostanie wyświetlona dostosowana lista działań przepływu pracy. Jednym z efektów ubocznych tego jest to, że jeśli dodano określone elementy domeny do **przybornika** za pomocą okna dialogowego **Wybierz elementy przybornika** , nadal będą widoczne te elementy, gdy pracujesz również w aplikacji konsolowej przepływu pracy. Jeśli nie chcesz ich zobaczyć, usuń je za pomocą menu kontekstowego lub usuń zaznaczenie ich w oknie dialogowym **Wybierz elementy przybornika** zgodnie z podanym opisem.

 Kolumny w tym oknie dialogowym zawierają następujące informacje:

 Nazwa wyświetla listę nazw działań przepływu pracy aktualnie zarejestrowanych na komputerze lokalnym.

 Przestrzeń nazw Wyświetla hierarchię przestrzeni nazw .NET Framework biblioteki klas, która definiuje strukturę działania.

 Nazwa zestawu zawiera nazwę i wersję zestawu .NET Framework zawierającego działanie.

 Katalog zawiera lokalizację zestawu .NET Framework zawierającego działania przepływu pracy. Domyślną lokalizacją dla wszystkich zestawów jest globalna pamięć podręczna zestawów.

 Aby posortować składniki, zaznacz dowolny nagłówek kolumny.