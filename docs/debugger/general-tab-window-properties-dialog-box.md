---
title: Karta Ogólne, okno dialogowe właściwości | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5160c79e2c8dae474927e6af7ebdc9e371e9edc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703230"
---
# <a name="general-tab-window-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości okna
Użyj **ogólne** kartę, aby wyświetlić informacje dotyczące wybranego okna. Aby wyświetlić [okno dialogowe właściwości](../debugger/window-properties-dialog-box.md), Przenieś fokus do [widoku Windows](../debugger/windows-view.md) okna. Zaznacz dowolny węzeł okna w drzewie, a następnie wybierz **właściwości** z **widoku** menu.

 Następujące ustawienia są dostępne na **ogólne** karty:

|Wpis|Opis|
|-----------|-----------------|
|**Tytuł okna**|Tekst w tytuł okna lub tekst zawarty w oknie, jeśli formant.|
|**Uchwyt okna**|Unikatowy identyfikator tego okna. Numery uchwyt okna są ponownie; identyfikują one oknem tylko okres istnienia tego okna.|
|**Proces okna**|Wirtualny adres funkcji procedury okna dla tego okna. To pole wskazuje również, czy to okno jest oknem Unicode i czy jest będące podklasami.|
|**Prostokąt**|Prostokąt otaczający okna. Rozmiar prostokąta jest również wyświetlany. Jednostki są pikseli współrzędne ekranu.|
|**Przywrócona Rect**|Prostokąt otaczający przywrócone okna. Rozmiar prostokąta jest również wyświetlany. Przywrócona prostokąt będzie różnią się od prostokąt, tylko wtedy, gdy okno jest zmaksymalizowane, lub zminimalizowana. Jednostki są pikseli współrzędne ekranu.|
|**Prostokąt klienta**|Prostokąt otaczający obszaru klienckiego okna. Rozmiar prostokąta jest również wyświetlany. Jednostki są względem lewej górnej części obszaru klienckiego okna w pikselach.|
|**Dojście wystąpienia**|Dojście wystąpienia aplikacji. Uchwyty wystąpienia nie są unikatowe.|
|**Identyfikator formantu lub uchwyt Menu**|Jeśli okno jest wyświetlane jest okno podrzędne, jest wyświetlana etykieta identyfikator kontrolki. Identyfikator formantu jest liczba całkowita, która identyfikuje identyfikator to okno podrzędne kontrolki. Jeśli okno jest wyświetlane nie jest oknem podrzędnym, jest wyświetlana etykiety Menu obsługi. Uchwyt menu jest liczbą całkowitą, która identyfikuje uchwyt menu skojarzone z tego okna.|
|**Dane użytkownika**|Dane specyficzne dla aplikacji, który jest dołączony do tej struktury okna.|
|**Bajty okna**|Liczba bajtów dodatkowej skojarzone z tego okna. Znaczenie tych bajtów jest określany przez aplikację. Rozwiń pole listy, aby wyświetlić wartości bajtów w formacie typu DWORD.|