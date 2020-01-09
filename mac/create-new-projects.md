---
title: Tworzenie nowych projektów i rozwiązań
description: W tym artykule opisano sposób tworzenia projektów i rozwiązań w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 10fcb52a8e1311f3e8128361ee835f6ddcb3670d
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2020
ms.locfileid: "75678903"
---
# <a name="create-a-new-project"></a>Utwórz nowy projekt

## <a name="opening-the-project-creation-dialog"></a>Otwieranie okna dialogowego tworzenia projektu

Istnieje kilka sposobów tworzenia nowego projektu w Visual Studio dla komputerów Mac. Po pierwszym otwarciu Visual Studio dla komputerów Mac zostanie wyświetlone okno Start. W tym miejscu możesz wybrać pozycję **Nowy** , która spowoduje przejście do ekranu tworzenia projektu.

> [!TIP]
> Ponadto, w oknie startowym można także otworzyć i wyszukać najnowsze projekty i rozwiązania. Możesz również otworzyć ostatnie projekty, przechodząc do paska menu i wybierając **plik > ostatnich rozwiązań**

![Okno uruchamiania z opcją Utwórz nowy projekt](media/first-run-project.png)

Jeśli Visual Studio dla komputerów Mac jest już otwarta z załadowanym rozwiązaniem, można utworzyć nowe rozwiązanie, przechodząc do paska menu i wybierając pozycję **plik > nowe rozwiązanie**. Tworzenie nowego rozwiązania w ten sposób zamyka już załadowane rozwiązanie.

## <a name="creating-a-new-project-from-a-template"></a>Tworzenie nowego projektu na podstawie szablonu

Domyślnie w oknie dialogowym **Nowy projekt** zostaną wyświetlone ostatnio używane szablony posortowane według *ostatnio używanych*.

Jeśli nie chcesz używać ostatnio używanego szablonu, możesz wybrać jedną z kategorii po lewej stronie okna dialogowego. Każda kategoria zawiera kilka szablonów projektu, które można wybrać. Kliknięcie typu projektu umożliwia wyświetlenie opisu po prawej stronie ekranu.

![Ekran nowy projekt](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurowanie nowego projektu

Po wybraniu szablonu projektu następujące ekrany przeprowadzi Cię przez kroki konfiguracji wymagane do skonfigurowania projektu; może się to różnić w zależności od typu projektu.

Wszystkie projekty wymagają nowego projektu wraz z lokalizacją do przechowywania plików. Jeśli projekt jest częścią nowego rozwiązania zamiast dodawania go do istniejącego rozwiązania, wymagana jest również nazwa rozwiązania.

Opcjonalnie na tym etapie można także skonfigurować opcje kontroli źródła git. Na poniższej ilustracji przedstawiono przykładowy krok konfiguracji końcowej dla projektu .NET Core:

![Konfigurowanie nowego projektu](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Dodawanie kolejnych projektów do rozwiązania

Aby dodać kolejne projekty do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie w okienko rozwiązania i wybierz opcję **dodaj > Dodaj nowy projekt** lub **Dodaj > Dodaj istniejący projekt**.

Dodanie nowego projektu przeprowadzi Cię przez proces tworzenia projektu, jak pokazano w temacie [Konfigurowanie nowego projektu](#configuring-your-new-project).

Wybranie opcji dodania istniejącego projektu umożliwi przejrzenie istniejącego projektu na komputerze i dodanie go do rozwiązania.

## <a name="see-also"></a>Zobacz także

- [Tworzenie rozwiązań i projektów (Visual Studio w systemie Windows)](/visualstudio/ide/creating-solutions-and-projects)
