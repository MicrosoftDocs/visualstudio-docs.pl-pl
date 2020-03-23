---
title: Tworzenie i edytowanie konfiguracji kompilacji
description: W tym artykule opisano tworzenie konfiguracji kompilacji w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128428"
---
# <a name="creating-and-editing-build-configurations"></a>Tworzenie i edytowanie konfiguracji kompilacji

Konfiguracje kompilacji zapewniają precyzyjną kontrolę nad kompilacją, co pozwala na tworzenie konfiguracji w celu uwzględnienia różnych sytuacji testowania i dystrybucji. Można tworzyć konfiguracje kompilacji dla poszczególnych projektów lub na podstawie całego rozwiązania.

Za pomocą okna dialogowego Opcje projektu można tworzyć nowe konfiguracje i edytować istniejące konfiguracje dla projektów i rozwiązań.

>[!NOTE]
>W tym temacie stosuje się do programu Visual Studio dla komputerów Mac. W programie Visual Studio w systemie Windows zobacz [Jak: Tworzenie i edytowanie konfiguracji](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Tworzenie konfiguracji kompilacji projektu

Aby utworzyć konfigurację kompilacji projektu, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Opcje**. Można również dwukrotnie kliknąć węzeł projektu, aby wywołać okno dialogowe Opcje projektu.

2. W oknie dialogowym Opcje projektu wybierz pozycję **Buduj > Konfiguracje:**

    ![Menedżer konfiguracji w opcjach projektu](media/create-and-edit-configurations-image2.png)

3. Wybierz **pozycję Dodaj,** aby utworzyć nową konfigurację. Można również skopiować dowolną z istniejących konfiguracji.

Po utworzeniu konfiguracji można użyć sekcji **Kompilacja** w opcjach projektu, aby dostosować właściwości odpowiednie do konfiguracji:

![Konfigurowanie opcji kompilacji](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Tworzenie konfiguracji kompilacji rozwiązania

Aby utworzyć konfigurację kompilacji rozwiązania, wykonaj następujące kroki:

1. Kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz polecenie **Opcje**. Można również dwukrotnie kliknąć węzeł rozwiązania, aby wywołać okno dialogowe Opcje rozwiązania.

2. W oknie dialogowym Opcje rozwiązania wybierz pozycję **Kompilacja > konfiguracje:**

    ![Menedżer konfiguracji w opcjach rozwiązania](media/create-and-edit-configurations-image1.png)

3. Wybierz **pozycję Dodaj,** aby utworzyć nową konfigurację. Można również skopiować dowolną z istniejących konfiguracji.

Po utworzeniu konfiguracji można użyć sekcji **Kompilacja** okna dialogowego Opcje projektu dla każdego projektu, aby dostosować właściwości odpowiednie do konfiguracji:

![Konfigurowanie opcji kompilacji](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Zmiana nazwy konfiguracji kompilacji

Aby zmienić nazwę konfiguracji, wybierz ją z listy Konfiguracja, przechodząc do **opcji Kompilacja > w opcjach** projektu lub rozwiązania:

![lista konfiguracji](media/create-and-edit-configurations-image4.png)

Wybierz przycisk **Zmień nazwę.**

![zmienianie nazwy okna dialogowego](media/create-and-edit-configurations-image5.png)

Następnie kliknij przycisk **OK,** aby potwierdzić.

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Zobacz też

- [Tworzenie i edytowanie konfiguracji kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)