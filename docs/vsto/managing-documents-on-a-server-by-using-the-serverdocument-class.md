---
title: Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
description: Dowiedz się, jak można użyć klasy ServerDocument w Visual Studio Tools dla środowiska uruchomieniowego pakietu Office, aby zarządzać kilkoma aspektami dostosowań na poziomie dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17a25ca382cfbbc762731afacaa628de616cfe1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879478"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
  `ServerDocument`Klasy w programie można użyć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do zarządzania kilkoma aspektami dostosowań na poziomie dokumentu, nawet jeśli nie zainstalowano programów Microsoft Office Word i Microsoft Office Excel. W tym miejscu można wykonywać następujące zadania:

- Dostęp do danych i ich modyfikowanie w pamięci podręcznej danych dokumentu lub skoroszytu. Aby uzyskać więcej informacji, zobacz [pracy z danymi buforowanymi w dokumencie](#CachedData).

- Zarządzanie zestawem dostosowywania skojarzonym z dokumentem. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostosowywaniem dokumentu](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Zrozumienie klasy ServerDocument
 `ServerDocument`Klasa jest przeznaczona do użycia na komputerach, na których nie zainstalowano pakietu Office. Z tego względu ta klasa jest zwykle używana w aplikacjach, które nie integrują się z pakietem Office, takich jak projekty konsoli lub projekty Windows Forms, a nie projekty pakietu Office. Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w zestawie *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

 `ServerDocument`Klasa może służyć do działania na dostosowania na poziomie dokumentu, które zostały utworzone przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Aby uzyskać więcej informacji na temat programu Visual Studio 2010 Tools for Office Runtime i rozszerzeń pakietu Office dla .NET Framework, zobacz temat [Visual Studio Tools for Office Runtime — Omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Jeśli masz starszą aplikację, która używa `ServerDocument` klasy w `Visual Studio Tools for Office` systemie (środowisko uruchomieniowe w wersji 3,0), `Visual Studio Tools for Office` system (wersja 3,0 Runtime) musi być zainstalowany na komputerach, na których działa aplikacja. `Visual Studio 2010 Tools for Office runtime`Nie można uruchamiać tych aplikacji.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Pracuj z danymi buforowanymi w dokumencie
 `ServerDocument`Klasa zawiera elementy członkowskie, których można użyć do pracy z pamięcią podręczną danych w dostosowanych dokumentach. Aby uzyskać więcej informacji na temat danych w pamięci podręcznej, zobacz [buforowanie danych](../vsto/caching-data.md) i [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).

 Poniższa tabela zawiera listę elementów członkowskich, których można użyć do pracy z danymi w pamięci podręcznej.

|Zadanie|Członek do użycia|
|----------|-------------------|
|Aby określić, czy dokument ma pamięć podręczną danych.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>Metoda.|
|Aby uzyskać dostęp do danych w pamięci podręcznej w dokumencie.<br /><br /> Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>Właściwość.|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Zarządzanie dostosowywaniem dokumentów
 Można użyć elementów członkowskich `ServerDocument` klasy do zarządzania zestawem dostosowań skojarzonym z dokumentem. Na przykład możesz programowo usunąć dostosowanie z dokumentu, tak aby dokument nie był już częścią dostosowania.

 W poniższej tabeli wymieniono elementy członkowskie, których można użyć do zarządzania zestawem dostosowywania.

|Zadanie|Członek do użycia|
|----------|-------------------|
|Aby określić, czy dokument jest częścią dostosowania na poziomie dokumentu.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>Metoda.|
|Aby programowo dołączyć dostosowanie do dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: dołączanie rozszerzeń kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Jedna z <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metod.|
|Aby programowo usunąć dostosowanie z dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: usuwanie rozszerzeń kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>Metoda.|
|Aby uzyskać adres URL manifestu wdrożenia, który jest skojarzony z dokumentem.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>Właściwość.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dołączanie rozszerzeń kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Instrukcje: usuwanie rozszerzeń kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Dane pamięci podręcznej](../vsto/caching-data.md)
