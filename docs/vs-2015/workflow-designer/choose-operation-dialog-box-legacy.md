---
title: Okno dialogowe Wybieranie operacji (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659162"
---
# <a name="choose-operation-dialog-box-legacy"></a>Wybieranie operacji, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia okna dialogowego **Wybieranie operacji** w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Okno dialogowe **Wybieranie operacji** służy do wybierania operacji do skojarzenia z <xref:System.Workflow.Activities.ReceiveActivity> działaniem lub <xref:System.Workflow.Activities.SendActivity> działaniem. Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego z tymi działaniami, zobacz [How to: Implementuj operację kontraktu WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) i [instrukcje: Wywołaj operację kontraktu WCF (starsza wersja)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Wybieranie operacji** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Dodaj kontrakt**|Tworzy nowy kontrakt. Możesz definiować nowe operacje na tym kontrakcie. (Jest to używane tylko z programem <xref:System.Workflow.Activities.ReceiveActivity> ).|
|**Dodaj operację**|Dodaje nowe operacje do nowego kontraktu, który został utworzony w oknie dialogowym **Wybieranie operacji** . **Uwaga:**  Nowe operacje można dodawać tylko do kontraktów utworzonych za pomocą okna dialogowego **Wybieranie operacji** . <br /><br /> (Jest to używane tylko z programem <xref:System.Workflow.Activities.ReceiveActivity> ).|
|**Importuj...**|Importuje wcześniej zdefiniowany kontrakt i umożliwia wybranie operacji z tego kontraktu.|
|**Nazwa operacji**|Nazwa aktualnie wybranej operacji. To pole tekstowe można edytować tylko wtedy, gdy utworzono operację za pomocą okna dialogowego **Wybieranie operacji** .|
|**Parametry**|Karta zawierająca definicje parametrów dla aktualnie wybranej operacji. **Uwaga:**  Definicje parametrów można zmienić tylko wtedy, gdy utworzono operację za pomocą okna dialogowego **Wybieranie operacji** .|
|**Właściwości**|Karta zawierająca <xref:System.Net.Security.ProtectionLevel> Ustawienia komunikatów wysyłanych między klientem i usługą. **Uwaga:**  Ta karta jest włączona tylko wtedy, gdy utworzono operację za pomocą okna dialogowego **Wybieranie operacji** .|
|**Uprawnienia**|Karta zawierająca <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> właściwości i użytkowników, którzy mogą wywołać tę operację. Jeśli na przykład tylko użytkownicy z grupy Administratorzy mogli wywołać tę operację, w polu tekstowym **rola** należy napisać "Administratorzy".<br /><br /> Na tej karcie włączono obsługę obu operacji utworzonych za pomocą okna dialogowego **ChooseOperation** oraz operacji zaimportowanych za pomocą przycisku **Importuj** .|

> [!NOTE]
> W oknie dialogowym **Wybieranie operacji** są wyświetlane tylko kontrakty lub operacje, które są używane przez inne <xref:System.Workflow.Activities.SendActivity> działania w przepływie pracy. Analogicznie, okno dialogowe **Wybieranie operacji** dla <xref:System.Workflow.Activities.ReceiveActivity> działań zawiera tylko kontrakty lub operacje, które są używane przez inne działania **odbierania** w przepływie pracy.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Implementowanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [instrukcje: wywoływanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [starszej wersji narzędzia do Windows Workflow Foundation interfejsu użytkownika](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)