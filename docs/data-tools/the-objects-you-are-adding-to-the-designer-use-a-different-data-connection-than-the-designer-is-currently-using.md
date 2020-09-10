---
title: Obiekty używają innego połączenia
description: Obiekty dodane do projektanta używają innego połączenia danych
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6394b31d7ace183e3fdb479988c7cc726f009bba
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743290"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Obiekty dodawane do projektanta używają innego połączenia danych niż Projektant

Obiekty dodawane do projektanta używają innego połączenia danych niż aktualnie używane przez projektanta. Czy chcesz zastąpić połączenie używane przez projektanta?

Po dodaniu elementów do **Object Relational Designer** (**Projektant O/R**) wszystkie elementy używają jednego połączenia danych udostępnionych. (Powierzchni projektowej reprezentuje <xref:System.Data.Linq.DataContext> , która używa jednego połączenia dla wszystkich obiektów na powierzchni). Po dodaniu obiektu do projektanta, który używa połączenia danych, które różni się od aktualnie używanego połączenia danych przez projektanta, ten komunikat zostanie wyświetlony. Aby rozwiązać ten problem, można wybrać, aby zachować istniejące połączenie. W przypadku wybrania tego wyboru wybrany obiekt nie zostanie dodany. Alternatywnie możesz dodać obiekt i zresetować <xref:System.Data.Linq.DataContext> połączenie z nowym połączeniem.

## <a name="connection-options"></a>Opcje połączenia

- Aby zastąpić istniejące połączenie z połączeniem używanym przez wybrany obiekt, kliknij przycisk **tak**.

   Wybrany obiekt jest dodawany do **projektanta O/R**, a element *DataContext. Connection* jest ustawiany na nowe połączenie.

   > [!NOTE]
   > Jeśli klikniesz przycisk **tak**, wszystkie klasy jednostek w **Projektancie O/R** są mapowane na nowe połączenie.

- Aby nadal korzystać z istniejącego połączenia i anulować Dodawanie zaznaczonego obiektu, kliknij przycisk **nie**.

   Akcja została anulowana. Element *DataContext. Connection* pozostaje ustawiony na istniejące połączenie.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
