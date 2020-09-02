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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977864"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
  Ten błąd jest wyświetlany podczas importowania regionu formularza zaprojektowanego w programie Outlook, ale co najmniej jedno pole w regionie formularza nie jest zgodne z klasami wiadomości wybieranymi na ostatniej stronie kreatora **nowego regionu formularza** .

Na przykład możesz wybrać **zadanie (IPM. Zadanie)** na ostatniej stronie kreatora **nowego regionu formularza** . Jeśli region formularza zawiera pole **adres służbowy** , zostanie wyświetlony następujący błąd, ponieważ zadanie nie ma adresu służbowego. W związku z tym pole **adres służbowy** nie jest zgodne z `IPM.Task` klasą wiadomości.

 Możesz wybrać **zadanie (IPM. Zadanie)** na ostatniej stronie kreatora **nowego regionu formularza** . Jeśli region formularza zawiera pole **adres służbowy** , zostanie wyświetlony następujący błąd, ponieważ zadanie nie ma adresu służbowego. W związku z tym pole **adres służbowy** nie jest zgodne z `IPM.Task` klasą wiadomości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Na ostatniej stronie kreatora **nowego regionu formularza** wybierz klasę komunikatów, która jest zgodna z polami w regionie formularza.

- W projektancie formularzy w programie Outlook usuń pola, które nie są zgodne z klasami komunikatów. Usuń pola, które planujesz wybrać na ostatniej stronie kreatora **nowego regionu formularza** .

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
