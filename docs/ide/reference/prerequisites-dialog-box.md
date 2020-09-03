---
title: Wstępnie wymagane składniki — Okno dialogowe
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf555a9a4b7c73e4e204bcc42e6b57d3ab96cd01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419175"
---
# <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe

W oknie dialogowym **wymagania wstępne** określono, które wstępnie wymagane składniki są zainstalowane, jak są instalowane, oraz kolejności instalacji pakietów.

![Okno dialogowe wymagania wstępne w programie Visual Studio](media/prerequisites-dialog-box.png)

Aby uzyskać dostęp do okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie wybierz **Project**  >  **Właściwości**projektu. Gdy zostanie wyświetlony **Projektant projektu** , wybierz kartę **Publikowanie** , a następnie wybierz pozycję **wymagania wstępne**. W przypadku projektów instalacyjnych w menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się okno dialogowe **strony właściwości** , kliknij pozycję **wymagania wstępne**.

## <a name="uielement-list"></a>Lista elementów UIElement

|Element|Opis|
|-------------|-----------------|
|**Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki**|Obejmuje składniki wymagane wstępnie w programie instalacyjnym aplikacji (*Setup.exe*), dzięki czemu zostaną one zainstalowane przed aplikacją w kolejności zależności. Ta opcja jest wybrana domyślnie. Jeśli to nie jest zaznaczone, *Setup.exe* nie zostanie utworzona.|
|**Wybierz wymagania wstępne do zainstalowania**|Określa, czy zainstalować składniki, takie jak .NET Framework i biblioteki środowiska uruchomieniowego języka C++.<br /><br />Na przykład, zaznaczając pole wyboru obok **SQL Server 2012 Express**, należy określić, że program instalacyjny musi sprawdzić, czy ten składnik jest zainstalowany na komputerze docelowym, i zainstalować go, jeśli nie.<br /><br />Aby uzyskać szczegółowe informacje na temat każdego wstępnie wymaganego pakietu, zobacz [Informacje o wymaganiach wstępnych](#prerequisites-information).|
|**Pobierz wstępnie wymagane składniki z witryny sieci Web dostawcy składników**|Określa, że wstępnie wymagane składniki mają być instalowane z witryny sieci Web dostawcy. Jest to domyślne ustawienie opcji.|
|**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co moja aplikacja**|Określa, że wstępnie wymagane składniki mają być instalowane z tej samej lokalizacji, w której znajduje się aplikacja. Spowoduje to skopiowanie wszystkich wstępnie wymaganych pakietów do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
|**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Określa, że wstępnie wymagane składniki mają być instalowane z wprowadzonej lokalizacji. Możesz użyć przycisku **Przeglądaj** , aby wybrać lokalizację.|

> [!NOTE]
> Aby uzyskać informacje na temat miejsca, w którym należy wprowadzić wymagania wstępne, zobacz [Tworzenie pakietów programu inicjującego](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informacje o wymaganiach wstępnych

Wstępnie wymagane składniki, które pojawiają się w oknie dialogowym **wymagania wstępne** , mogą się różnić od tych znajdujących się na poniższej liście. Wstępnie wymagane pakiety wymienione w **oknie dialogowym wymagania wstępne** są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli później zmienisz platformę docelową projektu, musisz ręcznie wybrać wymagania wstępne, aby dopasować nową platformę docelową.

|Element|Opis|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Ten pakiet instaluje następujące elementy:<br /><br /> -.NET Framework wersje 2,0, 3,0 i 3,5.<br />-Obsługa wszystkich wersji .NET Framework w systemach operacyjnych 32-bitowych (x86) i 64-bitowych (x64).<br />-Pakiety językowe dla każdej wersji .NET Framework, która jest zainstalowana z pakietem.<br />— Dodatki Service Pack dla .NET Framework 2,0 i 3,0.<br /><br /> .NET Framework 3,0 jest dołączony do systemu Windows Vista, a .NET Framework 3,5 jest dołączony do programu Visual Studio. .NET Framework 3,5 jest wymagany dla wszystkich projektów Visual Basic i C#, które są kompilowane dla 32-bitowych systemów operacyjnych i dla których platforma docelowa jest ustawiona na **.NET Framework 3,5**, a dla projektów Visual Basic i C# skompilowanych dla systemów operacyjnych 64-bitowego. (IA64 nie jest obsługiwana). Należy pamiętać, że projekty Visual Basic i C# są kompilowane domyślnie dla dowolnej architektury procesora. Aby uzyskać więcej informacji, zobacz temat [Omówienie określania elementów docelowych](../../ide/visual-studio-multi-targeting-overview.md) i [wdrażanie wymagań wstępnych dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4. x**|Ten pakiet instaluje .NET Framework 4. x dla platform x86 i x64.|
|**Typy Microsoft System CLR dla SQL Server 2014 (x64 i x86)**|Ten pakiet instaluje typy Microsoft System CLR dla SQL Server 2014 dla x64 lub x86.|
|**SQL Server 2008 R2 Express**|Ten pakiet instaluje Microsoft SQL Server 2008 R2 Express, bezpłatną wersję Microsoft SQL Server 2008 R2, idealną bazę danych dla małych aplikacji sieci Web, serwerów i komputerów. Może służyć bezpłatnie na potrzeby programowania i produkcji.|
|**SQL Server 2012 Express**|Ten pakiet instaluje Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Ten pakiet instaluje Microsoft SQL Server 2012 Express LocalDB.|
|**Biblioteki środowiska uruchomieniowego Visual C++ "14" (ARM)**|Ten pakiet instaluje Visual C++ biblioteki wykonawcze dla architektury Itanium, które zapewniają procedury programowania dla systemu operacyjnego Microsoft Windows. Procedury te automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez Języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dokumentacja biblioteki wykonawczej C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Biblioteki środowiska uruchomieniowego Visual C++ "14" (x64)**|Ten pakiet instaluje Visual C++ biblioteki uruchomieniowe dla systemów operacyjnych x64, które zapewniają procedury programowania dla systemu operacyjnego Microsoft Windows. Procedury te automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez Języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dokumentacja biblioteki wykonawczej C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Biblioteki środowiska uruchomieniowego Visual C++ "14" (x86)**|Ten pakiet instaluje Visual C++ biblioteki uruchomieniowe dla systemów operacyjnych x86, które zapewniają procedury programowania dla systemu operacyjnego Microsoft Windows. Procedury te automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez Języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dokumentacja biblioteki wykonawczej C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Zobacz też

- [Strona publikowania, Projektant projektu](../../ide/reference/publish-page-project-designer.md)
- [Wymagania wstępne dotyczące wdrażania aplikacji](../../deployment/application-deployment-prerequisites.md)
- [Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Omówienie określania celu platformy](../../ide/visual-studio-multi-targeting-overview.md)
