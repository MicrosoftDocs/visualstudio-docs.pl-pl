---
title: Obiekty dodawane do projektanta używają innego połączenia danych niż aktualnie używane przez projektanta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672300"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Obiekty dodawane do projektanta używają innego połączenia danych niż aktualnie używane przez projektanta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obiekty dodawane do projektanta używają innego połączenia danych niż aktualnie używane przez projektanta. Czy chcesz zastąpić połączenie używane przez projektanta?

 Po dodaniu elementów do [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) wszystkie elementy używają jednego połączenia danych udostępnionych. (Powierzchnia projektowa reprezentuje <xref:System.Data.Linq.DataContext>, która używa jednego połączenia dla wszystkich obiektów na powierzchni). Po dodaniu obiektu do projektanta, który używa połączenia danych, które różni się od aktualnie używanego połączenia danych przez projektanta, ten komunikat zostanie wyświetlony. Aby rozwiązać ten problem, można wybrać, aby zachować istniejące połączenie. W przypadku wybrania tego wyboru wybrany obiekt nie zostanie dodany. Alternatywnie możesz dodać obiekt i zresetować <xref:System.Data.Linq.DataContext> połączenie z nowym połączeniem.

> [!NOTE]
> Jeśli klikniesz przycisk **tak**, wszystkie klasy jednostek w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] są mapowane na nowe połączenie.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Aby zamienić istniejące połączenie z połączeniem używanym przez wybrany obiekt

- Kliknij przycisk **Tak**.

     Wybrany obiekt jest dodawany do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], a element DataContext. Connection jest ustawiany na nowe połączenie.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Aby nadal korzystać z istniejącego połączenia i anulować Dodawanie wybranego obiektu

- Kliknij przycisk **nie**.

     Akcja została anulowana. Element DataContext. Connection pozostaje ustawiony na istniejące połączenie.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)