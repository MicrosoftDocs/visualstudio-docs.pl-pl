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
ms.openlocfilehash: 6b13352ca54db84137e029aa126f1f174a1c80fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621477"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
  Ten błąd jest wyświetlany, gdy importowanie regionów formularzy zaprojektowanych w programie Outlook, ale co najmniej jedno pole na region formularza nie są zgodne z klas wiadomości, które można wybrać na ostatniej stronie **nowy Region formularza** kreatora.

Na przykład, możesz wybrać **zadań (IPM. Zadanie)** na ostatniej stronie **nowy Region formularza** kreatora. Jeśli region formularza ma **adres służbowy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres służbowy. W związku z tym **adres służbowy** pole nie jest zgodny z `IPM.Task` klasą wiadomości.

 Możesz wybrać **zadań (IPM. Zadanie)** na ostatniej stronie **nowy Region formularza** kreatora. Jeśli region formularza ma **adres służbowy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres służbowy. W związku z tym **adres służbowy** pole nie jest zgodny z `IPM.Task` klasą wiadomości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

-   Na ostatniej stronie **nowy Region formularza** kreatora, zaznacz klasę wiadomości, która jest zgodna z pól na region formularza.

-   W projektancie formularzy w programie Outlook usuń pola, które nie są zgodne z klas wiadomości. Usuń pola, które zamierzasz wybierz na ostatniej stronie **nowy Region formularza** kreatora.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
