---
title: Ustaw kontrolkę do utworzenia podczas przeciągania z okna źródła danych | Microsoft Docs
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
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 222ecfa56b179379c2d007e8635e7b40d6b1b660
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655382"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Formanty powiązane z danymi można tworzyć, przeciągając elementy z okna **źródła danych** do projektanta WPF lub projektanta Windows Forms. Każdy element w oknie **źródła danych** ma formant domyślny, który jest tworzony podczas przeciągania go do projektanta. Można jednak wybrać opcję utworzenia innej kontrolki.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Ustaw kontrolki do utworzenia dla tabel danych lub obiektów
 Przed przeciągnięciem elementów, które reprezentują tabele danych lub obiekty z okna **źródła danych** , można wybrać wyświetlanie wszystkich danych w jednej kontrolce lub wyświetlenie każdej kolumny lub właściwości w oddzielnym formancie.

 W tym kontekście *obiekt* Term odnosi się do niestandardowego obiektu biznesowego, jednostki (w Entity Data Model) lub obiektu zwróconego przez usługę.

#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Aby ustawić kontrolki do utworzenia dla tabel danych lub obiektów

1. Upewnij się, że jest otwarty projektant WPF lub Projektant Windows Forms.

2. W oknie **źródła danych** wybierz element reprezentujący tabelę danych lub obiekt, który ma zostać ustawiony.

3. Kliknij menu rozwijane dla elementu, a następnie kliknij jeden z następujących elementów w menu:

   - Aby wyświetlić każde pole danych w osobnej kontrolce, kliknij przycisk **szczegóły**. Po przeciągnięciu elementu danych do projektanta, ta akcja spowoduje utworzenie innej kontrolki powiązanej z danymi dla każdej kolumny lub właściwości nadrzędnej tabeli danych lub obiektu oraz etykiet dla każdej kontrolki.

   - Aby wyświetlić wszystkie dane w jednym formancie, wybierz inny formant na liście, taki jak **DataGrid** lub **list** w aplikacji WPF lub **DataGridView** w aplikacji Windows Forms.

     Lista dostępnych kontrolek zależy od tego, który z nich jest otwarty, która wersja .NET Framework obiektów docelowych projektu oraz czy dodano niestandardowe kontrolki, które obsługują powiązanie danych z **przybornikiem**. Jeśli formant, który chcesz utworzyć, znajduje się na liście dostępnych kontrolek, możesz dodać formant do listy. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Aby dowiedzieć się, jak utworzyć niestandardową kontrolkę Windows Forms, którą można dodać do listy formantów dla tabel danych lub obiektów w oknie **źródła danych** , zobacz [Tworzenie Windows Forms kontrolki użytkownika obsługującej złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Ustaw kontrolki do utworzenia dla kolumn danych lub właściwości
 Przed przeciągnięciem elementu, który reprezentuje kolumnę lub właściwość obiektu z okna **źródła danych** do projektanta, można ustawić formant, który ma zostać utworzony.

#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Aby ustawić kontrolki do utworzenia dla kolumn lub właściwości

1. Upewnij się, że jest otwarty projektant WPF lub Projektant Windows Forms.

2. W oknie **źródła danych** rozwiń żądaną tabelę lub obiekt, aby wyświetlić jego kolumny lub właściwości.

3. Zaznacz każdą kolumnę lub właściwość, dla której chcesz ustawić formant, który ma zostać utworzony.

4. Kliknij menu rozwijane dla kolumny lub właściwości, a następnie wybierz kontrolkę, którą chcesz utworzyć, gdy element zostanie przeciągnięty do projektanta.

     Lista dostępnych kontrolek zależy od tego, który z nich jest otwarty, która wersja .NET Framework obiektów docelowych projektu i które niestandardowe formanty obsługujące powiązanie danych zostało dodane do **przybornika**. Jeśli formant, który chcesz utworzyć, znajduje się na liście dostępnych kontrolek, możesz dodać formant do listy. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowych kontrolek do okna źródła danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Aby dowiedzieć się, jak utworzyć kontrolkę niestandardową, którą można dodać do listy formantów dla kolumn danych lub właściwości w oknie **źródła danych** , zobacz [Tworzenie Windows Forms kontrolki użytkownika obsługującej proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Jeśli nie chcesz tworzyć kontrolki dla kolumny lub właściwości, wybierz **Brak** z menu rozwijanego. Jest to przydatne, jeśli chcesz przeciągnąć tabelę nadrzędną lub obiekt do projektanta, ale nie chcesz uwzględniać konkretnej kolumny lub właściwości.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
