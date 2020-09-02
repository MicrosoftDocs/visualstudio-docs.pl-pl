---
title: Karta Ogólne, okno dialogowe Właściwości okna | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62849561"
---
# <a name="general-tab-window-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości okna
Karta **Ogólne** służy do wyświetlania informacji o wybranym oknie. Aby wyświetlić okno [dialogowe Właściwości okna](../debugger/window-properties-dialog-box.md), Przenieś fokus do okna [Widok systemu Windows](../debugger/windows-view.md) . Wybierz dowolny węzeł okna w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Na karcie **Ogólne** dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Podpis okna**|Tekst w podpisie okna lub tekst znajdujący się w oknie, jeśli jest to formant.|
|**Uchwyt okna**|Unikatowy identyfikator tego okna. Numery uchwytów okien są ponownie używane; identyfikują one okno tylko dla okresu istnienia tego okna.|
|**Proces okna**|Adres wirtualny funkcji procedury okna dla tego okna. To pole wskazuje również, czy to okno jest oknem Unicode i czy jest podklasą.|
|**Prostokąt**|Prostokąt ograniczający dla okna. Wyświetlany jest również rozmiar prostokąta. Jednostki są pikselami we współrzędnych ekranu.|
|**Przywrócony prostokąt**|Prostokąt ograniczający dla przywróconego okna. Wyświetlany jest również rozmiar prostokąta. Przywrócony prostokąt będzie się różnić w przypadku, gdy okno jest zmaksymalizowane lub zminimalizowane. Jednostki są pikselami we współrzędnych ekranu.|
|**Prostokąt klienta**|Prostokąt ograniczający obszar klienta okna. Wyświetlany jest również rozmiar prostokąta. Jednostki są pikselami względem lewego górnego rogu obszaru klienta okna.|
|**Dojście wystąpienia**|Dojście do wystąpienia aplikacji. Uchwyty wystąpienia nie są unikatowe.|
|**Identyfikator lub uchwyt menu kontrolki**|Jeśli wyświetlane okno jest oknem podrzędnym, zostanie wyświetlona etykieta identyfikator kontrolki. Identyfikator kontrolki jest liczbą całkowitą, która identyfikuje identyfikator formantu tego okna podrzędnego. Jeśli okno jest wyświetlane nie jest oknem podrzędnym, zostanie wyświetlona etykieta uchwytu menu. Uchwyt menu jest liczbą całkowitą, która identyfikuje uchwyt menu skojarzonego z tym oknem.|
|**Dane użytkownika**|Dane specyficzne dla aplikacji, które są dołączone do tej struktury okna.|
|**Bajty okna**|Liczba dodatkowych bajtów skojarzonych z tym oknem. Znaczenie tych bajtów jest określane przez aplikację. Rozwiń pole listy, aby wyświetlić wartości bajtów w formacie DWORD.|