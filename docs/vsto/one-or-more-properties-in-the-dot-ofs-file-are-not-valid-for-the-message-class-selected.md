---
title: Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095272"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
  Ten błąd jest wyświetlany, gdy importowanie regionów formularzy zaprojektowanych w programie Outlook, ale co najmniej jedno pole na region formularza nie są zgodne z klas wiadomości, które można wybrać na ostatniej stronie **nowy Region formularza** kreatora.

Na przykład, możesz wybrać **zadań (IPM. Zadanie)** na ostatniej stronie **nowy Region formularza** kreatora. Jeśli region formularza ma **adres służbowy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres służbowy. W związku z tym **adres służbowy** pole nie jest zgodny z `IPM.Task` klasą wiadomości.

 Możesz wybrać **zadań (IPM. Zadanie)** na ostatniej stronie **nowy Region formularza** kreatora. Jeśli region formularza ma **adres służbowy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres służbowy. W związku z tym **adres służbowy** pole nie jest zgodny z `IPM.Task` klasą wiadomości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Na ostatniej stronie **nowy Region formularza** kreatora, zaznacz klasę wiadomości, która jest zgodna z pól na region formularza.

- W projektancie formularzy w programie Outlook usuń pola, które nie są zgodne z klas wiadomości. Usuń pola, które zamierzasz wybierz na ostatniej stronie **nowy Region formularza** kreatora.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
