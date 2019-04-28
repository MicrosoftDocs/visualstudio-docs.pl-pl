---
title: Karta System.Activities, wybierz elementy przybornika — okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 29eb905a4852bf521ebee72a498b44edbdcef8df
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445406"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities, karta, Wybieranie elementów przybornika, okno dialogowe
Ta karta **wybierz elementy przybornika** okno dialogowe wyświetla listę [!INCLUDE[wf](../includes/wf-md.md)] działań, szablonów i elementów dostępnych dla Ciebie. Do wyświetlania tej listy, wybierz **wybierz elementy przybornika** z **narzędzia** menu lub klikając prawym przyciskiem myszy **przybornika** i wybierając polecenie **wybierz elementy**do wyświetlenia **wybierz elementy przybornika** okno dialogowe, a następnie wybierz jego **System.Activities** kartę. Gotowych lista zawiera działania przepływu pracy z zestawów System.Activities, System.ServiceModel.Activities i System.Activities.Core.Presentation; jednak tylko dostarczane przez system działania wyświetlane i działań, dodawać za pośrednictwem innych zestawów, wyświetlana w **przybornika** są zaznaczone domyślnie. Ostatnio dodane działań są automatycznie sprawdzane i są wyświetlane w **przybornika** po kliknięciu **OK** w oknie dialogowym. Ponadto te elementy są wyświetlane w **przybornika** pod nową kategorię, która odnosi się do przestrzeni nazw, gdzie znajduje się działanie / / szablon elementu.  
  
> [!WARNING]
> Jeśli spróbujesz dodać zestaw, który nie zawiera żadnych działań przepływu pracy, okna dialogowego błędu jest wyświetlany, który objaśnia, że zestaw nie zawiera żadnych działań.  
  
 To okno dialogowe jest niezależny od projektu i dlatego **System.Activities** kartę w dalszym ciągu wyświetlane w autonomicznych XAML lub typu projektu niezwiązanej z przepływem pracy.  
  
 Filtrowanie odbywa się na poszczególnych kartach. Oznacza to, nie jest możliwe dodawanie działań przepływu pracy za pośrednictwem **składnik .NET** kartę. Muszą oni można dodawać za pośrednictwem **System.Activities** samej karcie.  
  
 Możesz usunąć zaznaczenie wszelkich elementów, które nie mają być wyświetlane w **przybornika** z tego okna dialogowego kartę, lub też można to zrobić za pomocą **Usuń** menu kontekstowego w **przybornika** i usuwając odwołanie do zestawu nie powoduje usunięcia elementu z **przybornika**.  
  
 Utworzenie wystąpienia działania, przeciągając i upuszczając go w Projektancie dodaje zestaw, który zawiera element do listy przywoływanych zestawach automatycznie. Ponadto jeśli działania odwołuje się do zestawu języka C, nie dodaje C do listy przywoływanego zestawu. Zestaw C ma znajdować się w pamięci podręcznej GAC i tym samym katalogu co działanie B. W przypadku autonomicznego zestawu ma znajdować się w pamięci podręcznej GAC lub ścieżki sondy programu VS. Następnie można przeciągać i upuszczać działania na powierzchni projektanta przepływu pracy.  
  
 **Przybornik** ustawienia są domyślnie zapisywane jako opcje użytkownika, więc gdy następnym razem, gdy otworzysz **przybornika**, wyświetla listy niestandardowe działania przepływu pracy. Jeden efektem ubocznym tego jest to, że po dodaniu elementów do określonej domeny **przybornika** za pośrednictwem **wybierz elementy przybornika** okno dialogowe, możesz nadal przeglądać te elementy, jeśli pracujesz Aplikacja konsoli przepływu pracy oraz. Jeśli nie chcesz je wyświetlić, usuń je za pomocą menu kontekstowego lub usuń zaznaczenie pola wyboru je za pośrednictwem **wybierz elementy przybornika** okno dialogowe wspomniane wcześniej.  
  
 Kolumny w tym oknie dialogowym zawiera następujące informacje:  
  
 Nazwa  
 Wyświetla nazwy działania przepływu pracy w danym momencie zarejestrowany na komputerze lokalnym.  
  
 Przestrzeń nazw  
 Wyświetla hierarchię przestrzeni nazw w bibliotece klas .NET Framework, który definiuje strukturę działania.  
  
 Nazwa zestawu  
 Wyświetla nazwę i wersję zestawu .NET Framework, który zawiera działanie.  
  
 Katalog  
 Wyświetla lokalizację zestawu .NET Framework, który zawiera działania przepływu pracy. Domyślna lokalizacja dla wszystkich zestawów to Global Assembly Cache.  
  
 Aby posortować składniki na liście, wybierz nagłówek dowolnej kolumny.