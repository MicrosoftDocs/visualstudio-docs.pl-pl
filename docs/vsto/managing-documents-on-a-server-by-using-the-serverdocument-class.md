---
title: Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83f23bb04c9080b75d2a8e93252d981c0833d69d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630083"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
  Możesz użyć `ServerDocument` klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zarządzanie kilka aspektów dostosowywania poziomie dokumentu, nawet jeśli nie zainstalowano programu Microsoft Office Word i Microsoft Office Excel. Można wykonać następujące zadania:

- Dostęp i modyfikować dane w pamięci podręcznej danych w dokumencie lub skoroszycie. Aby uzyskać więcej informacji, zobacz [pracować dane w pamięci podręcznej w dokumencie](#CachedData).

- Zarządzaj zestaw dostosowania, który jest skojarzony z dokumentem. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostosowywania dokumentu](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Zrozumienie klasy ServerDocument
 `ServerDocument` Klasy jest przeznaczone do użytku na komputerach, które nie mają zainstalowanym pakietem Office. W związku zazwyczaj używasz tej klasy w aplikacjach, które nie są zintegrowane z pakietem Office, takich jak projekty startowe lub projektów Windows Forms, zamiast projektów pakietu Office. Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* zestawu.

 `ServerDocument` Klasa może być używana do wykonywania operacji dostosowywania na poziomie dokumentu, które zostały utworzone przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].

 Aby uzyskać więcej informacji o Visual Studio 2010 Tools for Office Runtime oraz rozszerzeń pakietu Office dla programu .NET Framework, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
>  Jeśli masz starszą aplikację, która używa `ServerDocument` klasy w `Visual Studio Tools for Office` system (w wersji 3.0 Runtime), `Visual Studio Tools for Office` system (wersja 3.0 runtime) musi być zainstalowany na komputerach z pakietem aplikacji. `Visual Studio 2010 Tools for Office runtime` Nie mogą uruchamiać tych aplikacji.

##  <a name="CachedData"></a> Praca z pamięci podręcznej danych w dokumencie
 `ServerDocument` Klasa oferuje elementy członkowskie, można użyć do pracy z pamięcią podręczną danych w dokumentach dostosowane. Aby uzyskać więcej informacji dotyczących buforowanych danych, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md) i [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).

 W poniższej tabeli wymieniono elementy członkowskie, które można użyć do pracy z danymi w pamięci podręcznej.

|Zadanie|Element członkowski do użycia|
|----------|-------------------|
|Aby określić, czy dokument ma pamięci podręcznej danych.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> Metody.|
|Aby uzyskać dostęp do pamięci podręcznej danych w dokumencie.<br /><br /> Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Właściwości.|

##  <a name="CustomizationInfo"></a> Zarządzanie dostosowywania dokumentu
 Można użyć elementów członkowskich `ServerDocument` klasy do zarządzania zestaw dostosowania, który jest skojarzony z dokumentem. Na przykład można programowo usunąć dostosowania z dokumentu, aby dokument nie jest już częścią dostosowania.

 W poniższej tabeli wymieniono elementy członkowskie, których można użyć do zarządzania zestaw dostosowania.

|Zadanie|Element członkowski do użycia|
|----------|-------------------|
|Aby określić, czy dokument jest częścią dostosowywania poziomie dokumentu.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> Metody.|
|Aby programowo dołączyć dostosowanie do dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Dołączanie rozszerzenia kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Jedną z <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody.|
|Aby programowo usunąć dostosowania dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Usuwanie kodu zarządzanego rozszerzenia z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> Metody.|
|Aby uzyskać adres URL manifestu wdrażania, który jest skojarzony z dokumentem.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> Właściwości.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dołączanie rozszerzenia kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Instrukcje: Usuwanie rozszerzenia kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Dane w pamięci podręcznej](../vsto/caching-data.md)
