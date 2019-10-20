---
title: Powiązywanie kontrolek z obrazami z bazy danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b8f6ee192399c8af8a508b2f9c2817db954bb36
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673015"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Powiązywanie kontrolek z obrazami z bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć okna **źródła danych** , aby powiązać obraz w bazie danych z kontrolką w aplikacji. Na przykład można powiązać obraz z kontrolką <xref:System.Windows.Controls.Image> w aplikacji WPF lub z kontrolką <xref:System.Windows.Forms.PictureBox> w aplikacji Windows Forms.

 Obrazy w bazie danych są zwykle przechowywane jako tablice bajtowe. Elementy w oknie **źródła danych** , które są przechowywane jako tablice bajtowe mają typ kontroli ustawiony domyślnie na **none** , ponieważ tablice bajtowe mogą zawierać wszystko z prostej tablicy bajtów do pliku wykonywalnego dużej aplikacji. Aby utworzyć kontrolkę powiązaną z danymi dla elementu tablicy bajtów w oknie **źródła danych** , które reprezentuje obraz, należy wybrać kontrolkę, która ma zostać utworzona.

 W poniższej procedurze przyjęto założenie, że okno **źródła danych** jest już wypełnione elementem, który jest powiązany z obrazem.

## <a name="bind-a-picture-in-a-database-to-a-control"></a>Powiązywanie obrazu w bazie danych z kontrolką

1. Upewnij się, że powierzchnia projektowa, do której chcesz dodać formant, jest otwarta w projektancie WPF lub Projektant formularzy systemu Windows.

2. W oknie **źródła danych** rozwiń żądaną tabelę lub obiekt, aby wyświetlić jego kolumny lub właściwości.

3. Wybierz kolumnę lub właściwość, która zawiera dane obrazu, a następnie wybierz jedną z następujących kontrolek z listy rozwijanej kontrolki:

    - Jeśli Projektant WPF jest otwarty, wybierz pozycję **obraz**.

    - Jeśli projektant Windows Forms jest otwarty, wybierz opcję **PictureBox**.

    - Alternatywnie możesz wybrać inny formant, który obsługuje powiązanie danych i który może wyświetlać obrazy. Jeśli formant, którego chcesz użyć, nie znajduje się na liście dostępnych kontrolek, możesz dodać go do listy, a następnie wybrać. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
