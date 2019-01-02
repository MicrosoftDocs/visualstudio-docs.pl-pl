---
title: Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d6469c48def1a5d21eb160cb4ad6d14704bc101
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909128"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
  Ten błąd jest wyświetlany, gdy importowanie regionów formularzy zaprojektowanych w programie Outlook, ale co najmniej jedno pole na region formularza nie są zgodne z klas wiadomości, które można wybrać na ostatniej stronie **nowy Region formularza** kreatora.  

Na przykład, możesz wybrać **zadań (IPM. Zadanie)** na ostatniej stronie **nowy Region formularza** kreatora. Jeśli region formularza ma **adres służbowy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres służbowy. W związku z tym **adres służbowy** pole nie jest zgodny z `IPM.Task` klasą wiadomości.  
  
 Możesz wybrać **zadań (IPM. Zadanie)** na ostatniej stronie **nowy Region formularza** kreatora. Jeśli region formularza ma **adres służbowy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres służbowy. W związku z tym **adres służbowy** pole nie jest zgodny z `IPM.Task` klasą wiadomości.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Na ostatniej stronie **nowy Region formularza** kreatora, zaznacz klasę wiadomości, która jest zgodna z pól na region formularza.  
  
-   W projektancie formularzy w programie Outlook usuń pola, które nie są zgodne z klas wiadomości. Usuń pola, które zamierzasz wybierz na ostatniej stronie **nowy Region formularza** kreatora.  
  
## <a name="see-also"></a>Zobacz także  
 [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
