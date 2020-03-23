---
title: Tworzenie nowych projektów i rozwiązań
description: W tym artykule opisano sposób tworzenia projektów i rozwiązań w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 10fcb52a8e1311f3e8128361ee835f6ddcb3670d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75678903"
---
# <a name="create-a-new-project"></a>Tworzenie nowego projektu

## <a name="opening-the-project-creation-dialog"></a>Otwieranie okna dialogowego tworzenia projektu

Istnieje kilka sposobów tworzenia nowego projektu w programie Visual Studio dla komputerów Mac. Po pierwszym otwarciu programu Visual Studio dla komputerów Mac zostanie wyświetlone okno startowe. W tym miejscu możesz wybrać **nowy,** który przeniesie Cię do ekranu tworzenia projektu.

> [!TIP]
> Ponadto od okna startowego można również otwierać i wyszukiwać najnowsze projekty i rozwiązania. Możesz również otworzyć najnowsze projekty, przechodząc do paska menu i wybierając **opcję Plik > Najnowsze rozwiązania**

![Okno Start z utworzeniem nowego projektu](media/first-run-project.png)

Jeśli program Visual Studio dla komputerów Mac jest już otwarty z załadowanym rozwiązaniem, można utworzyć nowe rozwiązanie, przechodząc do paska menu i wybierając **polecenie Plik > nowe rozwiązanie**. Tworzenie nowego rozwiązania w ten sposób zamyka rozwiązanie, które jest już załadowane.

## <a name="creating-a-new-project-from-a-template"></a>Tworzenie nowego projektu z szablonu

Domyślnie w oknie dialogowym **Nowy projekt** zostaną wyświetlone ostatnio używane szablony posortowane według *ostatnio używanych*.

Jeśli nie chcesz używać najnowszego szablonu, możesz wybrać jedną z kategorii po lewej stronie okna dialogowego. Każda kategoria zawiera kilka szablonów projektów do wyboru. Kliknięcie typu projektu umożliwia wyświetlenie opisu po prawej stronie ekranu.

![Nowy ekran projektu](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurowanie nowego projektu

Po wybraniu szablonu projektu na ekranach zostaną wyświetlone wszystkie kroki konfiguracji wymagane do skonfigurowania projektu; może się to różnić w zależności od typu projektu.

Wszystkie projekty wymagają nowego projektu, wraz z lokalizacją do przechowywania plików. Jeśli projekt jest częścią nowego rozwiązania, a nie dodanie go do istniejącego rozwiązania, nazwa rozwiązania będzie również wymagane.

Opcjonalnie na tym etapie można również skonfigurować opcje sterowania źródłem Git. Poniższy obraz jest przykładem końcowego kroku konfiguracji dla projektu .NET Core:

![Konfigurowanie nowego projektu](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Dodawanie dodatkowych projektów do rozwiązania

Dodatkowe projekty można dodać do rozwiązania, klikając prawym przyciskiem myszy rozwiązanie w panelu rozwiązania i wybierając opcję **Dodaj > Dodaj nowy projekt** lub Dodaj > Dodaj **istniejący projekt.**

Dodanie nowego projektu spowoduje przejście przez tworzenie projektu, jak pokazano w [konfiguracji nowego projektu](#configuring-your-new-project).

Wybranie opcji dodawania istniejącego projektu umożliwia przeglądanie istniejącego projektu na komputerze i dodawanie go do rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozwiązań i projektów (Visual Studio w systemie Windows)](/visualstudio/ide/creating-solutions-and-projects)
