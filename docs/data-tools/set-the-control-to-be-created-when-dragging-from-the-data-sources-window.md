---
title: Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f43219cc5329b46cdaba052a9f46709ee0af406f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565987"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych

Możesz utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na projektanta WPF lub projektanta Windows Forms. Każdy element na **źródeł danych** okno ma domyślny formant, który jest tworzony podczas przeciągania do projektanta. Można utworzyć innej kontrolki.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Ustawienie kontroli ma zostać utworzony dla tabel danych lub obiektów

Podczas przeciągania elementów, które reprezentują tabele danych lub obiektów z **źródeł danych** okna, możesz wybrać do wyświetlania wszystkich danych w jednym formancie, lub do wyświetlania każdej kolumny lub właściwości w oddzielnej kontrolce.

W tym kontekście pojęcie *obiektu* odwołuje się do obiektu niestandardowego biznesowego, jednostki (w modelu Entity Data Model) lub Obiekt zwrócony przez usługę.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Aby ustawić formanty, które ma zostać utworzony dla tabel danych lub obiektów

1. Upewnij się, **WPF** projektanta lub **Windows Forms** Projektant jest otwarty.

2. W **źródeł danych** okna, wybierz element, który reprezentuje tabeli danych lub obiekt, którego chcesz ustawić.

   > [!TIP]
   > Jeśli **źródeł danych** okno nie jest otwarty, możesz go otworzyć, wybierając **widoku** > **Windows inne** > **źródeł danych**.

3. Kliknij przycisk menu rozwijanej dla elementu, a następnie kliknij jedną z następujących elementów w menu:

    - Aby wyświetlić poszczególnych pól w oddzielnej kontrolce, kliknij przycisk **szczegóły**. Podczas przeciągania elementu danych do projektanta, ta akcja spowoduje utworzenie innej kontrolki powiązane z danymi dla każdej kolumny lub właściwości nadrzędnej danych tabeli lub obiektu oraz etykiety dla każdego formantu.

    - Aby wyświetlić wszystkie dane w jednym formancie, Wybieranie innej kontrolki na liście, takie jak **DataGrid** lub **listy** w aplikacji WPF lub **DataGridView** w formularzach Windows Forms aplikacja.

    Lista dostępnych kontrolek jest zależny, na których projektant otwartych, która wersja programu .NET Framework projekt jest ukierunkowany i tego, czy zostały dodane niestandardowe formanty danych pomocy technicznej powiązanie **przybornika**. Jeśli formant, który chcesz utworzyć, nie jest lista dostępnych kontrolek, możesz dodać formant do listy. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Aby dowiedzieć się, jak można utworzyć niestandardowego formantu Windows Forms, który można dodać do listy formanty tabele danych lub obiekty na liście **źródeł danych** okna, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje złożonych danych Powiązanie](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Ustawienie kontroli ma zostać utworzony dla właściwości lub kolumn danych

Przed przeciągnięciem elementu, który reprezentuje kolumny lub właściwości obiektu **źródeł danych** okna projektanta, można ustawić formant, który ma zostać utworzony.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Aby ustawić formanty, które ma zostać utworzony dla kolumny lub właściwości

1. Upewnij się, **WPF** projektanta lub **Windows Forms** Projektant jest otwarty.

2. W **źródeł danych** okna, rozwiń odpowiednią tabelę lub obiekt, aby wyświetlić jej właściwości lub kolumn.

3. Wybierz każdej kolumny lub właściwości, dla którego chcesz ustawić formant, który ma zostać utworzony.

4. Kliknij menu rozwijane dla kolumny lub właściwości, a następnie wybierz formant, który chcesz utworzyć, gdy element zostanie przeciągnięty do projektanta.

     Lista dostępnych kontrolek jest zależny, na których projektant otwartych, która wersja programu .NET Framework projekt jest ukierunkowany i które niestandardowe formanty obsługujące, możesz powiązania danych zostały dodane do **przybornika**. Jeśli formant, który ma zostać utworzona lista dostępnych kontrolek, możesz dodać formant do listy. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych formantów do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Aby dowiedzieć się, jak utworzyć formant niestandardowy, który można dodać do listy formantów dla kolumn danych lub właściwości w **źródeł danych** okna, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Jeśli nie chcesz utworzyć formant do kolumny lub właściwości, wybierz opcję **Brak** w menu rozwijanym. Jest to przydatne, jeśli chcesz przeciągnąć do projektanta tabeli nadrzędnej lub obiekt, ale nie chcesz dołączyć określonej kolumny lub właściwości.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)