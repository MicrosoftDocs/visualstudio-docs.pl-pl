---
title: Tworzenie nowych projektów i rozwiązań
description: W tym artykule opisano sposób tworzenia projektów i rozwiązań w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: dbfc0d951524bb9ffbbd4a2366679cfc6ae41925
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693064"
---
# <a name="creating-a-new-project"></a>Tworzenie nowego projektu

## <a name="opening-the-project-creation-dialog"></a>Otwierając okno dialogowe tworzenia projektu

Istnieje kilka sposobów, aby utworzyć nowy projekt w programie Visual Studio dla komputerów Mac. Przy pierwszym otwarciu programu Visual Studio dla komputerów Mac, zostanie wyświetlony ekran powitalny. W tym miejscu można wybrać **New** co spowoduje przejście do ekranu tworzenia projektu.

> [!TIP]
> Ponadto na ekranie powitalnym, można również otworzyć i wyszukaj ostatnie projekty i rozwiązania. Możesz również otworzyć ostatnich projektów, przechodząc do paska menu i wybierając **Plik > najnowsze rozwiązania**

![Ekran powitalny zawierający Utwórz nowy projekt](media/first-run-project.png)

Jeśli program Visual Studio for Mac jest już otwarty z rozwiązaniem, który został załadowany, można utworzyć nowe rozwiązanie, przechodząc do paska menu i wybierając **Plik > nowe rozwiązanie**. Tworzenie nowego rozwiązania w ten sposób spowoduje zamknięcie rozwiązania, który jest już załadowany.

## <a name="creating-a-new-project-from-a-template"></a>Tworzenie nowego projektu z szablonu

**Nowy projekt** okno dialogowe, domyślnie pokaże posortowane według ostatnio używanych szablonów *ostatnio używanych*.

Jeśli chcesz użyć szablonu ostatnie, można wybrać z listy kategorii po lewej stronie okna dialogowego. Każda kategoria zawiera kilka szablonów projektów służących do wyboru. Kliknięcie typu projektu, można wyświetlić opis po prawej stronie ekranu.

![Nowy ekran projektu](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurowanie nowego projektu

Po wybraniu szablonu projektu następującym zrzucie ekranu wykonasz wszelkie czynności konfiguracyjne wymagane do skonfigurowania projektu; to może się różnić od typu projektu.

Wszystkie projekty wymagają nowego projektu oraz lokalizację do zapisania plików. Jeśli projekt jest częścią nowego rozwiązania, zamiast dodawania go do istniejącego rozwiązania, nazwy rozwiązania będzie również wymagane.

Opcjonalnie na tym etapie można również skonfigurować opcje kontroli źródła Git. Poniższy rysunek jest przykładem ostatnim etapem konfiguracji dla projektu .NET Core:

![Konfigurowanie nowego projektu](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Dodawanie dodatkowe projekty do rozwiązania

Możesz dodać dodatkowe projekty do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie, w konsoli rozwiązania, a następnie wybierając opcję **Dodaj > Dodaj nowy projekt** lub **Dodaj > Dodaj istniejący projekt**.

Dodawanie nowego projektu poprowadzi Cię przez proces tworzenia projektu, jak pokazano na [konfigurowania nowego projektu](#configuring-your-new-project).

Wybierając pozycję Dodaj istniejący projekt umożliwia przeglądanie w poszukiwaniu istniejącego projektu na komputerze i dodaj go do rozwiązania.

## <a name="see-also"></a>Zobacz także

- [Tworzenie rozwiązań i projektów (Visual Studio Windows)](/visualstudio/ide/creating-solutions-and-projects)