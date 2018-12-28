---
title: Powiązywanie kontrolek z obrazami z bazy danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e50a3126407c9306e2a1f00a411e08f69c69602
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647070"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Powiązywanie kontrolek z obrazami z bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Możesz użyć **źródeł danych** okna obrazu w bazie danych można powiązać kontrolki w aplikacji. Na przykład, można powiązać obraz <xref:System.Windows.Controls.Image> kontroli w aplikacji WPF lub do <xref:System.Windows.Forms.PictureBox> kontrolki w aplikacji Windows Forms.  
  
 Obrazy w bazie danych są zazwyczaj przechowywane jako tablice typu byte. Elementy w **źródeł danych** okna, które są przechowywane jako tablice typu byte kontrolujesz ich typ równa **Brak** domyślnie, ponieważ tablice bajtów może zawierać wszystko, od prostej tablicy bajtów do pliku wykonywalnego dużych aplikacji. Aby utworzyć formant powiązany z danymi elementu tablicy bajtów w **źródeł danych** okno, które reprezentuje obraz, należy wybrać formant do utworzenia.  
  
 W poniższej procedurze przyjęto, że **źródeł danych** okna jest już wypełniony elementu, który jest powiązany z obrazu.
  
## <a name="bind-a-picture-in-a-database-to-a-control"></a>Powiązania obrazu w bazie danych do kontrolki  
  
1.  Upewnij się, że chcesz dodać formant do powierzchni projektowej jest otwarty w Projektancie WPF lub projektanta Windows Forms.  
  
2.  W **źródeł danych** okna, rozwiń odpowiednią tabelę lub obiekt, aby wyświetlić jej właściwości lub kolumn.  
  
3.  Wybierz kolumny lub właściwości, które zawiera dane obrazu, a następnie wybierz jedną z następujących formantów z listy rozwijanej kontrolki:  
  
    -   Projektant WPF jest otwarty, wybierz opcję **obraz**.  
  
    -   Jeśli projektant Windows Forms jest otwarty, wybierz **PictureBox**.  
  
    -   Alternatywnie można wybrać innej kontrolki obsługującej powiązanie danych i które można wyświetlać obrazy. Jeśli formant, który chcesz użyć, nie jest lista dostępnych kontrolek, możesz dodać go do listy, a następnie wybierz ją. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
