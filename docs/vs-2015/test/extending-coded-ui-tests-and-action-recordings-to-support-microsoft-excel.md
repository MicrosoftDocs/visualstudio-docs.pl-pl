---
title: Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji do obsługi programu Microsoft Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a48c01203d2e951e917482de3c0d9c2bec29ae01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660572"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Struktura testowania dla kodowanych testów interfejsu użytkownika i nagrań akcji nie obsługuje każdego możliwego interfejsu użytkownika. Może nie obsługiwać określonego interfejsu użytkownika, który ma zostać przetestowany. Na przykład nie można natychmiast utworzyć kodowanego testu interfejsu użytkownika lub rejestrowania akcji dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] arkusza kalkulacyjnego. Można jednak utworzyć własne rozszerzenie dla struktury kodowanego testu interfejsu użytkownika, która będzie obsługiwała konkretny interfejs użytkownika, wykorzystując rozszerzalność kodowanego środowiska testowania interfejsu użytkownika. Poniższy temat zawiera przykład sposobu rozszerzającej strukturę programu w celu obsługi tworzenia kodowanych testów interfejsu użytkownika i nagrań akcji dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Aby uzyskać więcej informacji na temat obsługiwanych platform, zobacz [obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

 **Requirements**

- Visual Studio Enterprise

  W tej sekcji przedstawiono rozszerzenie kodowanego testu interfejsu użytkownika, które umożliwia rejestrowanie i odtwarzanie testów w arkuszach programu Excel. Każda część rozszerzenia została omówiona w tej sekcji i komentarze do kodu dla deweloperów, którzy chcą utworzyć takie rozszerzenie.

  ![Architektura testu interfejsu użytkownika](../test/media/ui-testarch.png "UI_TestArch") Przegląd architektury

## <a name="download-the-sample"></a>Pobierz przykład
 Przykład składa się z czterech projektów w `CodedUIExtensibilitySample.sln` rozwiązaniu:

- CodedUIextensibilitySample

- ExcelCodedUIAddInHelper

- ExcelUICommunicationHelper

- SampleTestProject

  Pobierz przykład z tego [wpisu w blogu](http://go.microsoft.com/fwlink/?LinkID=185592).

> [!NOTE]
> Przykład jest przeznaczony do użycia z programem Microsoft Excel 2010. Przykład może współdziałać z innymi wersjami programu Microsoft Excel, ale nie jest obecnie obsługiwany.

## <a name="details-about-the-sample"></a>Szczegóły przykładu
 Poniższe sekcje zawierają informacje dotyczące przykładu i jego struktury.

### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Dodatek programu Microsoft Excel: ExcelCodedUIAddinHelper
 Ten projekt zawiera dodatek, który działa w procesie programu Excel. Zobacz [Przykładowy dodatek programu Excel dla kodowanych testów interfejsu użytkownika](../test/sample-excel-add-in-for-coded-ui-testing.md) , aby zapoznać się z krótkim omówieniem projektu dodatku.

 Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f).

### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Komunikacja interfejsu użytkownika programu Excel: ExcelUIcommunicationHelper
 Ten projekt zawiera interfejs `IExcelUICommunication` i klasy informacji, które są używane do przekazywania danych między strukturą kodowanego testowania interfejsu użytkownika i programem Excel. Aby uzyskać więcej informacji, zobacz [przykładowy interfejs programu Excel Communicator](../test/sample-excel-communicator-interface.md).

### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Rozszerzenie kodowanego testu interfejsu użytkownika: CodedUIExentsibilitySample
 Ten projekt zawiera klasy niestandardowe, które są używane w testach arkusza programu Excel. Kod dla każdej z tych klas jest dość oczywisty. Jednak udostępniamy Krótki opis każdej klasy niestandardowej. Aby uzyskać więcej informacji, zobacz [przykładowe rozszerzenie kodowanego testu interfejsu użytkownika dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).

### <a name="deploying-your-add-in-and-extension"></a>Wdrażanie dodatku i rozszerzenia
 Po utworzeniu wszystkich projektów i obiektów Uruchom udostępniony plik `CopyDrop.bat` jako administrator. Ten plik kopiuje `ExcelCodedUIAddinHelper` DLL i plików PDB do programu:

 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", gdzie numer wersji to 11,0, 12,0 itd. w oparciu o wersję programu Visual Studio.

 Pliki DLL `ExcelUICommunicationHelper` i PDB są kopiowane do `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.

 Może być konieczne dostosowanie dokładnej ścieżki kopii, ale nie jest wymagana żadna dodatkowa Instalacja. Na komputerze 64-bitowym należy użyć wiersza polecenia 32-bitowy Visual Studio Enterprise, aby uruchomić `CopyDrop.bat` plik.

### <a name="testing-excel-with-the-sampletestproject"></a>Testowanie programu Excel przy użyciu SampleTestProject
 Test można uruchomić w podanym projekcie testowym, który używa określonej wersji programu Excel, która nie istnieje, lub utworzyć własny projekt testowy i nagrać test własny. Aby uzyskać więcej informacji, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
