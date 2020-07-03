---
title: Tworzenie i edytowanie konfiguracji kompilacji
description: W tym artykule opisano Tworzenie konfiguracji kompilacji w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: eb3ceed624e3bbba67564bb8f7c359841c0e496d
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939188"
---
# <a name="creating-and-editing-build-configurations"></a>Tworzenie i edytowanie konfiguracji kompilacji

Konfiguracje kompilacji zapewniają precyzyjną kontrolę nad kompilacją, co pozwala na tworzenie konfiguracji w celu uwzględnienia różnych sytuacji testowania i dystrybucji. Można tworzyć konfiguracje kompilacji dla poszczególnych projektów lub na podstawie całego rozwiązania.

Można tworzyć nowe konfiguracje i edytować istniejące dla projektów i rozwiązań za pomocą okna dialogowego Opcje projektu.

>[!NOTE]
>Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows Zapoznaj [się z tematem How to: Create and Edit Configurations](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Tworzenie konfiguracji kompilacji projektu

Aby utworzyć konfigurację kompilacji projektu, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Opcje**. Możesz również kliknąć dwukrotnie węzeł projektu, aby wyświetlić okno dialogowe Opcje projektu.

2. W oknie dialogowym Opcje projektu wybierz pozycję **kompilacje > konfiguracje**:

    ![Menedżer konfiguracji w opcjach projektu](media/create-and-edit-configurations-image2.png)

3. Wybierz pozycję **Dodaj** , aby utworzyć nową konfigurację. Możesz również skopiować dowolne istniejące konfiguracje.

Po utworzeniu konfiguracji można użyć sekcji **kompilacja** w opcjach projektu, aby dostosować właściwości odpowiednie dla danej konfiguracji:

![Konfigurowanie opcji kompilacji](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Tworzenie konfiguracji kompilacji rozwiązania

Aby utworzyć konfigurację kompilacji rozwiązania, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Opcje**. Możesz również kliknąć dwukrotnie węzeł rozwiązania, aby wyświetlić okno dialogowe Opcje rozwiązania.

2. W oknie dialogowym Opcje rozwiązania wybierz pozycję **kompilacje > konfiguracje**:

    ![Menedżer konfiguracji w opcjach rozwiązania](media/create-and-edit-configurations-image1.png)

3. Wybierz pozycję **Dodaj** , aby utworzyć nową konfigurację. Możesz również skopiować dowolne istniejące konfiguracje.

Po utworzeniu konfiguracji można użyć sekcji **kompilacja** w oknie dialogowym Opcje projektu dla każdego projektu, aby dostosować właściwości odpowiednie dla danej konfiguracji:

![Konfigurowanie opcji kompilacji](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Zmiana nazwy konfiguracji kompilacji

Aby zmienić nazwę konfiguracji, wybierz ją z listy konfiguracji, przechodząc do opcji **Kompilowanie konfiguracji >** w programie Project lub rozwiązania:

![Lista konfiguracji](media/create-and-edit-configurations-image4.png)

Wybierz przycisk **Zmień nazwę** .

![Zmień nazwę okna dialogowego](media/create-and-edit-configurations-image5.png)

Następnie kliknij przycisk **OK** , aby potwierdzić.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Zobacz też

- [Tworzenie i edytowanie konfiguracji kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)