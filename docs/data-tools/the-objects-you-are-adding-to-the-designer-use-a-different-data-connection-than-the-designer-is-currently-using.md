---
title: Obiekty dodawane do projektanta używają innego połączenia danych niż aktualnie używane przez projektanta
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e0864ec07250ed5886f864d4233aeb902ecf5ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565625"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Obiekty, dodawane do projektanta używają innego połączenia danych niż projektanta

Obiekty, które są dodawane do projektanta Użyj innego połączenia danych niż aktualnie używane projektanta. Czy chcesz zastąpić połączenie używane przez projektanta?

Podczas dodawania elementów do **Object Relational Designer** (**O/R Designer**), wszystkie elementy, użyj jednego połączenia danych udostępnionych. (Na powierzchnię projektową reprezentuje <xref:System.Data.Linq.DataContext>, który używa pojedynczego połączenia dla wszystkich obiektów na powierzchni.) Ten komunikat pojawia się po dodaniu obiektu do projektanta, który korzysta z połączenia danych, która różni się od połączenia danych są obecnie używane przez projektanta. Aby rozwiązać ten problem, można zachować istniejące połączenie. W przypadku wprowadzenia ten wybór nie można dodać wybranego obiektu. Alternatywnie można dodać obiektu i zresetuj <xref:System.Data.Linq.DataContext> połączenia do nowego połączenia.

## <a name="connection-options"></a>Opcje połączenia

- Aby zastąpić istniejące połączenie połączenie używane przez wybrany obiekt, kliknij przycisk **tak**.

   Zaznaczony obiekt zostanie dodany do **O/R Designer**i *DataContext.Connection* jest ustawiona na nowe połączenie.

   > [!NOTE]
   > Jeśli klikniesz **tak**, klas wszystkie jednostki w **O/R Designer** są mapowane na nowe połączenie.

- Aby nadal korzystać z istniejącego połączenia i anulowania Dodawanie wybranego obiektu, kliknij przycisk **nie**.

   Akcja została anulowana. *DataContext.Connection* pozostanie wartość istniejącego połączenia.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
