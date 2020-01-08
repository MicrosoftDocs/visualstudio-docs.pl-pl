---
title: Powiązywanie kontrolek z obrazami z bazy danych
ms.date: 11/04/2016
ms.topic: conceptual
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a4155a246516bef074a56e5644712912b2ce5af6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587007"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Powiązywanie kontrolek z obrazami z bazy danych

Możesz użyć okna **źródła danych** , aby powiązać obraz w bazie danych z kontrolką w aplikacji. Na przykład można powiązać obraz z kontrolką <xref:System.Windows.Controls.Image> w aplikacji WPF lub z kontrolką <xref:System.Windows.Forms.PictureBox> w aplikacji Windows Forms.

Obrazy w bazie danych są zwykle przechowywane jako tablice bajtowe. Elementy w oknie **źródła danych** , które są przechowywane jako tablice bajtowe mają typ kontroli ustawiony domyślnie na **none** , ponieważ tablice bajtowe mogą zawierać wszystko z prostej tablicy bajtów do pliku wykonywalnego dużej aplikacji. Aby utworzyć kontrolkę powiązaną z danymi dla elementu tablicy bajtów w oknie **źródła danych** , które reprezentuje obraz, należy wybrać kontrolkę, która ma zostać utworzona.

W poniższej procedurze przyjęto założenie, że okno **źródła danych** jest już wypełnione elementem, który jest powiązany z obrazem.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Aby powiązać obraz w bazie danych z kontrolką

1. Upewnij się, że powierzchnia projektowa, do której chcesz dodać formant, jest otwarta w projektancie WPF lub Projektant formularzy systemu Windows.

2. W oknie **źródła danych** rozwiń żądaną tabelę lub obiekt, aby wyświetlić jego kolumny lub właściwości.

   > [!TIP]
   > Jeśli okno **źródła danych** nie jest otwarte, otwórz je, wybierając opcję **wyświetl** > inne > **źródła danych** **systemu Windows** .

3. Wybierz kolumnę lub właściwość, która zawiera dane obrazu, a następnie wybierz jedną z następujących kontrolek z listy rozwijanej kontrolki:

    - Jeśli Projektant WPF jest otwarty, wybierz pozycję **obraz**.

    - Jeśli projektant Windows Forms jest otwarty, wybierz opcję **PictureBox**.

    - Alternatywnie możesz wybrać inny formant, który obsługuje powiązanie danych i który może wyświetlać obrazy. Jeśli formant, którego chcesz użyć, nie znajduje się na liście dostępnych kontrolek, możesz dodać go do listy, a następnie wybrać. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
