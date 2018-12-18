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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d93ca95a67bc3816d8d65a799282dc6c7969e093
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304920"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Powiązywanie kontrolek z obrazami z bazy danych

Możesz użyć **źródeł danych** okna obrazu w bazie danych można powiązać kontrolki w aplikacji. Na przykład, można powiązać obraz <xref:System.Windows.Controls.Image> kontroli w aplikacji WPF lub do <xref:System.Windows.Forms.PictureBox> kontrolki w aplikacji Windows Forms.

Obrazy w bazie danych są zazwyczaj przechowywane jako tablice typu byte. Elementy w **źródeł danych** okna, które są przechowywane jako tablice typu byte kontrolujesz ich typ równa **Brak** domyślnie, ponieważ tablice bajtów może zawierać wszystko, od prostej tablicy bajtów do pliku wykonywalnego dużych aplikacji. Aby utworzyć formant powiązany z danymi elementu tablicy bajtów w **źródeł danych** okno, które reprezentuje obraz, należy wybrać formant do utworzenia.

W poniższej procedurze przyjęto, że **źródeł danych** okna jest już wypełniony elementu, który jest powiązany z obrazu.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Obraz w bazie danych można powiązać kontrolki

1.  Upewnij się, że chcesz dodać formant do powierzchni projektowej jest otwarty w Projektancie WPF lub projektanta Windows Forms.

2.  W **źródeł danych** okna, rozwiń odpowiednią tabelę lub obiekt, aby wyświetlić jej właściwości lub kolumn.

   > [!TIP]
   > Jeśli **źródeł danych** okno nie jest otwarte, otwórz go, wybierając **widoku** > **Windows inne** > **źródeł danych**.

3.  Wybierz kolumny lub właściwości, które zawiera dane obrazu, a następnie wybierz jedną z następujących formantów z listy rozwijanej kontrolki:

    - Projektant WPF jest otwarty, wybierz opcję **obraz**.

    - Jeśli projektant Windows Forms jest otwarty, wybierz **PictureBox**.

    - Alternatywnie można wybrać innej kontrolki obsługującej powiązanie danych i które można wyświetlać obrazy. Jeśli formant, który chcesz użyć, nie jest lista dostępnych kontrolek, możesz dodać go do listy, a następnie wybierz ją. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)