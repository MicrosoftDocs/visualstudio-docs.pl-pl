---
title: Obiekty są dodawane do projektanta używają innego połączenia danych, niż projektanta jest aktualnie używane | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fa80118fc6eca31603832882db2d6aa16cd9d21
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647073"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Obiekty dodawane do projektanta używają innego połączenia danych niż aktualnie używane przez projektanta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Obiekty, które są dodawane do projektanta Użyj innego połączenia danych niż aktualnie używane projektanta. Czy chcesz zastąpić połączenie używane przez projektanta?  
  
 Podczas dodawania elementów do [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), wszystkie elementy, użyj jednego połączenia danych udostępnionych. (Na powierzchnię projektową reprezentuje <xref:System.Data.Linq.DataContext>, który używa pojedynczego połączenia dla wszystkich obiektów na powierzchni.) Ten komunikat pojawia się po dodaniu obiektu do projektanta, który korzysta z połączenia danych, która różni się od połączenia danych są obecnie używane przez projektanta. Aby rozwiązać ten problem, można zachować istniejące połączenie. W przypadku wprowadzenia ten wybór nie można dodać wybranego obiektu. Alternatywnie można dodać obiektu i zresetuj <xref:System.Data.Linq.DataContext> połączenia do nowego połączenia.  
  
> [!NOTE]
>  Jeśli klikniesz **tak**, klas wszystkie jednostki w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] są mapowane na nowe połączenie.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Aby zastąpić istniejące połączenie połączenie używane przez wybrany obiekt  
  
-   Kliknij przycisk **Tak**.  
  
     Zaznaczony obiekt zostanie dodany do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], a DataContext.Connection jest ustawiona na nowe połączenie.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Aby nadal korzystać z istniejącego połączenia i anulowania Dodawanie wybranego obiektu  
  
-   Kliknij przycisk **nie**.  
  
     Akcja została anulowana. Pozostanie DataContext.Connection wartość istniejącego połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   