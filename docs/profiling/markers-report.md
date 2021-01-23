---
title: Raport znaczników | Microsoft Docs
description: Dowiedz się, jak raport znaczniki wyświetla listę znaczników w wyświetlanym czasie i jak przesuwanie lub powiększanie może powodować występowanie lub znikanie znaczników.
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
ms.openlocfilehash: 7e95cf3b14f804c481ff03ec6fbf72b360efedc7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722116"
---
# <a name="markers-report"></a>Raport dotyczący znaczników
Raport znaczniki wyświetla listę znaczników w wyświetlanym czasie.  Kadrowanie lub powiększanie lub ukrywanie ścieżek może spowodować, że znaczniki będą widoczne lub znikane. Raport zawiera te informacje o każdym znaczniku:

- Godzina rozpoczęcia śledzenia, odnosząca się do początku.

- Jego czas trwania. Czas trwania flag i komunikatów jest równy zero, ponieważ reprezentuje on natychmiastowe.

- Identyfikator wątku, który go wygenerował.

- Dostawca śledzenia zdarzeń dla systemu Windows (ETW), który go wygenerował.

- Seria znaczników, z której został zapisany.

- Kategoria zdarzeń, do której należy.

- Jego poziom ważności.

- Jego typ (zakres, flaga lub komunikat).

- Ogólny opis tego, co reprezentuje

  Wybierz przycisk **Eksportuj** , aby zapisać raport znaczników jako plik CSV. Możesz użyć danych z pliku CSV z innymi aplikacjami lub narzędziami.

> [!NOTE]
> Raport znaczników może zawierać 1 000 znaczników. Aby wyświetlić wszystkie znaczniki, należy wyeksportować pełny raport do pliku CSV.