---
title: Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4852dc5b65f00f7d298f5f1a15d39ff041022578
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791995"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Struktura testowania kodowane testy interfejsu użytkownika i nagrywania akcji nie obsługuje Każdy przykładowy interfejs użytkownika. Nie obsługuje określonego interfejsu użytkownika, który ma zostać przetestowana. Na przykład nie można bezpośrednio utworzyć kodowany test interfejsu użytkownika lub nagranie akcji dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] arkusza kalkulacyjnego. Można jednak utworzyć własne rozszerzenie struktury kodowanych testów interfejsu użytkownika, obsługujące określonych interfejs użytkownika dzięki wykorzystaniu możliwości rozszerzania Framework kodowanego testu interfejsu użytkownika. Poniższy temat przedstawiono przykładowy sposób rozszerzyć środowisko obsługuje tworzenie kodowanych testów interfejsu użytkownika i nagrywania akcji dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Aby uzyskać więcej informacji na temat platform, które są obsługiwane, zobacz [obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
  W tej sekcji przedstawiono kodowane rozszerzenia testu interfejsu użytkownika, który można nagrywać i odtwarzać testy w arkuszu kalkulacyjnym programu Excel. Każda część rozszerzenie zostało wyjaśnione w tej sekcji i w komentarzach do kodu dla deweloperów, którzy chcą tworzyć tylko takie rozszerzenie.  
  
  ![Architektura testu interfejsu użytkownika](../test/media/ui-testarch.png "UI_TestArch")  
  Omówienie architektury  
  
## <a name="download-the-sample"></a>Pobierz przykład  
 Przykład składa się z czterema projektami w `CodedUIExtensibilitySample.sln` rozwiązania:  
  
- CodedUIextensibilitySample  
  
- ExcelCodedUIAddInHelper  
  
- ExcelUICommunicationHelper  
  
- SampleTestProject  
  
  Pobierz próbkę z tego [wpis w blogu](http://go.microsoft.com/fwlink/?LinkID=185592).  
  
> [!NOTE]
>  Przykład jest przeznaczony do użytku z programem Microsoft Excel 2010. Próbki mogą działać z innymi wersjami programu Microsoft Excel, ale nie jest obecnie obsługiwane.  
  
## <a name="details-about-the-sample"></a>Szczegółowe informacje o przykładzie  
 Poniższe sekcje zawierają informacje o przykładu i jego strukturę.  
  
### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Microsoft dodatek programu Excel: ExcelCodedUIAddinHelper  
 Ten projekt zawiera dodatek, który działa w procesie programu Excel. Zobacz [przykładowy dodatek Excel dla kodowanych testów interfejsu użytkownika](../test/sample-excel-add-in-for-coded-ui-testing.md) krótki przegląd projektu dodatku.  
  
 Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f).  
  
### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Komunikacja interfejsu użytkownika programu Excel: ExcelUIcommunicationHelper  
 Ten projekt zawiera `IExcelUICommunication` interfejsu i klasy informacje, które są używane do przekazywania danych między struktury testowania kodowanego interfejsu użytkownika i program Excel. Aby uzyskać więcej informacji, zobacz [interfejs komunikatora programu Excel przykładowe](../test/sample-excel-communicator-interface.md).  
  
### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Rozszerzenie testu kodowanego interfejsu użytkownika: CodedUIExentsibilitySample  
 Ten projekt zawiera niestandardowych klas, które są używane w testach arkusza programu Excel. Kod dla każdego z tych klas jest dość oczywiste. Jednak firma Microsoft zapewnia krótki opis każdej klasy niestandardowej. Aby uzyskać więcej informacji, zobacz [rozszerzenie kodowanych testów interfejsu użytkownika przykładowe dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
### <a name="deploying-your-add-in-and-extension"></a>Wdrażanie usługi dodatku i rozszerzenia  
 Po utworzeniu wszystkich projektów i obiekty, uruchom podane `CopyDrop.bat` pliku jako administrator. Kopiuje ten plik `ExcelCodedUIAddinHelper` plików DLL i pliku PDB do:  
  
 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", gdzie numer wersji może być 11.0, 12.0 itp., zależnie od wersji programu Visual Studio.  
  
 `ExcelUICommunicationHelper` DLL i pliku PDB, pliki są kopiowane do `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.  
  
 Może być konieczne dostosowanie ścieżki dokładna kopia, ale instalacja dodatkowych nie jest wymagane. Na komputerze 64-bitowym, należy użyć 32-bitowy wiersz polecenia programu Visual Studio Enterprise do uruchomienia `CopyDrop.bat` pliku.  
  
### <a name="testing-excel-with-the-sampletestproject"></a>Testowanie programu Excel z SampleTestProject  
 Możesz uruchomić test w projekcie testowym podana, który używa określonej wersji programu Excel może nie mieć, lub utworzenie projektu testowego i nagraj test własne. Aby uzyskać więcej informacji, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
