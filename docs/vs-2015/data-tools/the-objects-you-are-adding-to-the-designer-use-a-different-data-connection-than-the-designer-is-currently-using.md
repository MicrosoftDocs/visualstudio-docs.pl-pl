---
title: Obiekty są dodawane do projektanta używają innego połączenia danych, niż projektanta jest aktualnie używane | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 773d3ea2e0d5574b194a44783b14d35db25d6f7f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661831"
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