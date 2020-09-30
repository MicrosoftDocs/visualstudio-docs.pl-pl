---
title: Nieprawidłowe właściwości w pliku. ofs dla klasy Message "
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
ms.openlocfilehash: 66e8ecacffb58e945a3f80d03f47edc1329668d1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584662"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Nieprawidłowe właściwości w pliku. ofs dla klasy Message

  Błąd "co najmniej jedna właściwość w pliku OFS jest nieprawidłowa dla wybranej klasy komunikatu" pojawia się podczas importowania regionu formularza zaprojektowanego w programie Outlook, ale co najmniej jedno pole w regionie formularza nie jest zgodne z klasami komunikatów wybranymi na ostatniej stronie kreatora **nowego regionu formularza** .

Na przykład możesz wybrać **zadanie (IPM. Zadanie)** na ostatniej stronie kreatora **nowego regionu formularza** . Jeśli region formularza zawiera pole **adres służbowy** , zostanie wyświetlony następujący błąd, ponieważ zadanie nie ma adresu służbowego. W związku z tym pole **adres służbowy** nie jest zgodne z `IPM.Task` klasą wiadomości.

 Możesz wybrać **zadanie (IPM. Zadanie)** na ostatniej stronie kreatora **nowego regionu formularza** . Jeśli region formularza zawiera pole **adres służbowy** , zostanie wyświetlony następujący błąd, ponieważ zadanie nie ma adresu służbowego. W związku z tym pole **adres służbowy** nie jest zgodne z `IPM.Task` klasą wiadomości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Na ostatniej stronie kreatora **nowego regionu formularza** wybierz klasę komunikatów, która jest zgodna z polami w regionie formularza.

- W projektancie formularzy w programie Outlook usuń pola, które nie są zgodne z klasami komunikatów. Usuń pola, które planujesz wybrać na ostatniej stronie kreatora **nowego regionu formularza** .

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
