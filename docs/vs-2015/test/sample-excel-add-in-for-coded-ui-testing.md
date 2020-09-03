---
title: Przykładowy dodatek programu Excel dla kodowanych testów interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6dc6b4385130c6341b5b3545c6c9f71dc67457f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672197"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Przykładowy dodatek Excel dla kodowanych testów UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przykładowy dodatek dla programu [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] został zaprojektowany specjalnie w celu obsługi kodowanych testów interfejsu użytkownika arkuszy programu Excel, które są rejestrowane i uruchamiane w Visual Studio Enterprise. Dodatek jest tworzony przy użyciu Visual Studio Tools pakietu Office.

 Aby uzyskać więcej informacji na temat sposobu tworzenia dodatku dla programu Excel, zobacz [Przewodnik: Tworzenie pierwszego dodatku VSTO dla programu Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) lub wyszukiwanie w witrynie MSDN dla "dodatku dla programu Excel".

 Mimo że dodatek programu Excel nie jest podstawowym tematem tej dokumentacji rozszerzenia kodowanego testu interfejsu użytkownika dla programu Excel, przydatne może być kilka komentarzy.

 Ważne części tego dodatku:

- `ThisAddIn`  Klasa — zarządza kanałem komunikacji zdalnej .NET między `ExcelUICommunicator` i [przykładowym rozszerzeniem kodowanego testu interfejsu użytkownika dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).

- `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  -Certyfikat zabezpieczeń do testowania dodatku.

- `ExcelUICommunicator`  Klasa — ta klasa implementuje `IExcelUICommunication` interfejs.

## <a name="thisaddin-class"></a>Klasa ThisAddIn
 Większość tej klasy jest generowana przez Visual Studio Tools pakietu Office w `ThisAddIn.Designer.cs` pliku podczas tworzenia projektu dodatku programu Excel.

 Elementy członkowskie, które należy zaimplementować, to programy obsługi zdarzeń: `ThisAddIn_Startup()` i `ThisAddIn_Shutdown()` . Ich celem jest zainicjowanie lub zamknięcie kanału komunikacji zdalnej .NET używanego przez program `ExcelUICommunicator` .

## <a name="excelcodeduiaddinhelper_temporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey. pfx
 Ten plik zawiera tymczasowy certyfikat zabezpieczeń wygenerowany przez Visual Studio Tools pakietu Office i nadaje uprawnienia zestawu dodatku do działania w procesie programu Excel na potrzeby testowania dodatku i rozszerzenia. Należy usunąć ten certyfikat i utworzyć nowy na karcie **podpisywanie** okna **Właściwości** projektu lub dołączyć własny certyfikat testowy.

## <a name="exceluicommunicator-class"></a>Klasa ExcelUICommunicator
 Ta klasa implementuje `IExcelUITestCommunication` interfejs i pobiera informacje o żądanym interfejsie użytkownika z modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [przykładowy interfejs programu Excel Communicator](../test/sample-excel-communicator-interface.md).

## <a name="see-also"></a>Zobacz też
 [Rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji w celu obsługi przewodnika programu Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [: Tworzenie pierwszego dodatku narzędzi VSTO dla programów Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) [i programowanie SharePoint](https://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)
