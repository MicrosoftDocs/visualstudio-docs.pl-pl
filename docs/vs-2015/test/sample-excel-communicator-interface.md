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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660492"
---
# <a name="sample-excel-communicator-interface"></a>Interfejs komunikatora programu Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przykładowy interfejs `IExcelUICommunication` jest używany w obiekcie `ExcelUICommunicator` w projekcie `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>IExcelUICommunication, interfejs
 Ten interfejs definiuje punkty komunikacji między `CodedUIExtension`, które są uruchamiane w procesie kodowanego testu interfejsu użytkownika i `ExcelCodedUIAddIn`, które są uruchamiane w procesie [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

 Zestaw `ExcelCodedUIAddinHelper` ma klasę `ExcelUICommunicator`, która dziedziczy z tego interfejsu i używa modelu obiektów programu Excel do przetwarzania metod.

 Niektóre metody pobierają żądane informacje z programu Excel, a następnie tworzą i zwracają jeden z obiektów informacji, takich jak `CellInformation` obiektu.

 Inne metody używają dostarczonego obiektu informacji, Znajdź odpowiednią kontrolkę w programie Excel i wykonaj jakiś proces na formancie. Na przykład Metoda `ScrollIntoView` przewija arkusz, aby była widoczna wypisana komórka.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample i ExcelCodedUIAddinHelper
 Zestaw `ExcelCodedUIAddinHelper` jest uruchamiany w procesie programu Excel i ma klasę `UICommunicator`, która implementuje interfejs `IExcelUITestCommunication` i Pobiera lub ustawia wymagane informacje bezpośrednio z interfejsu użytkownika programu Excel.

 Zestaw `CodedUIExtensibilitySample` jest uruchamiany w procesie kodowanego testu interfejsu użytkownika programu Visual Studio. Ten zestaw ma klasę `Communicator`, która otwiera kanał komunikacji zdalnej .NET i udostępnia Właściwość `Instance`, która używa interfejsu `IExcelUICommunication` do używania obiektu `UICommunicator` w zestawie `ExcelCodedUIAddinHelper` do przekazywania żądań i obiektów informacji , takie jak `CellInformation` obiektu, między dwoma zestawami.

## <a name="see-also"></a>Zobacz też
 [Rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji na potrzeby obsługi](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [przykładowego dodatku programu Microsoft Excel dla KODOWANYch testów interfejsu](../test/sample-excel-add-in-for-coded-ui-testing.md) użytkownika [przykładowe kodowane testy dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md)
