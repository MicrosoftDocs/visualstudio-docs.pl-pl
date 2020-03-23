---
title: Raport znaczników | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9502d2cf0081985cfbee2283af820c06d681ad9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "64808272"
---
# <a name="markers-report"></a>Raport dotyczący znaczników
Raport znaczników zawiera listę znaczników w wyświetlonym przedziale czasowym.  Przesuwanie, powiększanie lub ukrywanie pasów ruchu może spowodować pojawienie się lub zniknięcie znaczników. Raport zawiera te informacje o każdym znaczniku:

- Czas, kiedy się rozpoczął, w stosunku do początku śledzenia.

- Jego czas trwania. Czas trwania wynosi zero dla flag i wiadomości, ponieważ reprezentują one chwilę.

- Identyfikator wątku, który go wygenerował.

- Dostawca śledzenia zdarzeń dla systemu Windows (ETW), który go wygenerował.

- Seria znaczników, z której została napisana.

- Kategoria zdarzeń, do której należy.

- Jego poziom ważności.

- Jego typ (zakres, flaga lub wiadomość).

- Opis wysokiego poziomu tego, co reprezentuje

  Wybierz przycisk **Eksportuj,** aby zapisać raport znaczników jako plik CSV. Dane w pliku CSV można używać z innymi aplikacjami lub narzędziami.

> [!NOTE]
> Raport znaczników może wyświetlać 1000 znaczników. Aby wyświetlić wszystkie znaczniki, wyeksportuj pełny raport do pliku CSV.