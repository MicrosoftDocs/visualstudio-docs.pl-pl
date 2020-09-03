---
title: Przykładowy interfejs programu Excel Communicator | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e3a9bd037c8886743910af649bf831b11337598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660492"
---
# <a name="sample-excel-communicator-interface"></a>Interfejs komunikatora programu Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przykładowy `IExcelUICommunication` interfejs jest używany w `ExcelUICommunicator` obiekcie w `ExcelAddIn` projekcie.

## <a name="iexceluicommunication-interface"></a>IExcelUICommunication, interfejs
 Ten interfejs definiuje punkty komunikacji między programem `CodedUIExtension` , który działa w procesie kodowanego testu interfejsu użytkownika i `ExcelCodedUIAddIn` , który działa w [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] procesie.

 `ExcelCodedUIAddinHelper`Zestaw ma `ExcelUICommunicator` klasę, która dziedziczy z tego interfejsu i używa modelu obiektów programu Excel do przetwarzania metod.

 Niektóre metody pobierają żądane informacje z programu Excel, a następnie tworzą i zwracają jeden z obiektów informacji, takich jak `CellInformation` obiekt.

 Inne metody używają dostarczonego obiektu informacji, Znajdź odpowiednią kontrolkę w programie Excel i wykonaj jakiś proces na formancie. Na przykład `ScrollIntoView` Metoda przewija arkusz w taki sposób, aby wyświetlona komórka była widoczna.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample i ExcelCodedUIAddinHelper
 `ExcelCodedUIAddinHelper`Zestaw jest uruchamiany w procesie programu Excel i ma `UICommunicator` klasę, która implementuje `IExcelUITestCommunication` interfejs i Pobiera lub ustawia wymagane informacje bezpośrednio z interfejsu użytkownika programu Excel.

 `CodedUIExtensibilitySample`Zestaw jest uruchamiany w procesie kodowanego testu interfejsu użytkownika programu Visual Studio. Ten zestaw ma `Communicator` klasę, która otwiera kanał komunikacji zdalnej .NET, i udostępnia `Instance` Właściwość, która używa `IExcelUICommunication` interfejsu do używania `UICommunicator` obiektu w `ExcelCodedUIAddinHelper` zestawie do przekazywania żądań i obiektów informacji, takich jak `CellInformation` obiekt, z powrotem i do przodu między dwoma zestawami.

## <a name="see-also"></a>Zobacz też
 [Rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji na potrzeby obsługi](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [przykładowego dodatku programu Microsoft Excel dla KODOWANYch testów interfejsu](../test/sample-excel-add-in-for-coded-ui-testing.md) użytkownika [przykładowe kodowane testy dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md)
