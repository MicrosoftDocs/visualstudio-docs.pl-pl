---
title: Podstawowa usługa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409715"
---
# <a name="service-essentials"></a>Podstawowe informacje o usłudze
Usługa jest umową między dwoma pakietów VSPackage. Jeden pakietu VSPackage udostępnia określony zestaw interfejsów dla innego pakietu VSPackage do użycia. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] to sama kolekcja pakietów VSPackage, która udostępnia usługi innym pakietów VSPackage.

 Można na przykład użyć usługi SVsActivityLog do uzyskania interfejsu IVsActivityLog, którego można użyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [How to: Use the Activity Log](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia również niektóre wbudowane usługi, które nie są zarejestrowane. Pakietów VSPackage może zastąpić wbudowane lub inne usługi, dostarczając przesłonięcie usługi. Dla każdej usługi dozwolony jest tylko jedno przesłonięcie usługi.

 Usługi nie mają możliwości odnajdowania. W związku z tym należy znać identyfikator usługi (SID) usługi, która ma zostać zużyta, i należy wiedzieć, które interfejsy zapewnia. Dokumentacja referencyjna usługi zawiera te informacje.

- Pakietów VSPackage świadczący usługi są nazywane dostawcami usług.

- Usługi udostępniane innym pakietów VSPackage są nazywane usługami globalnymi.

- Usługi, które są dostępne tylko dla pakietu VSPackage, które je implementują, lub do dowolnego tworzonego obiektu, są nazywane usługami lokalnymi.

- Usługi, które zastępują wbudowane usługi lub usługi udostępniane przez inne pakiety, są nazywane zastępowaniem usługi.

- Usług lub zastąpień usługi są ładowane na żądanie, czyli dostawca usług jest ładowany, gdy usługa, którą zapewnia, jest wymagana przez inny pakietu VSPackage.

- Aby zapewnić obsługę ładowania na żądanie, dostawca usług rejestruje swoje usługi globalne przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [How to: zapewnianie usługi](../../extensibility/how-to-provide-a-service.md).

- Po uzyskaniu usługi należy użyć [polecenia QueryInterface](/cpp/atl/queryinterface) (kod niezarządzany) lub rzutowania (kod zarządzany) w celu uzyskania odpowiedniego interfejsu, na przykład:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Zarządzany kod odnosi się do usługi według jej typu, natomiast niezarządzany kod odnosi się do usługi za pomocą identyfikatora GUID.

- Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje pakietu VSPackage, przekazuje dostawcę usług do pakietu VSPackage, aby dać pakietu VSPackage dostęp do usług globalnych. Jest to nazywane "lokalizacjami" pakietu VSPackage.

- Pakietów VSPackage mogą być dostawcami usług dla tworzonych przez siebie obiektów. Na przykład formularz może wysłać żądanie dotyczące usługi kolorowej do ramki, co może przekazać żądanie do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Zarządzane obiekty, które są głęboko zagnieżdżone lub nie znajdują się w ogóle, mogą wywoływać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>, aby uzyskać bezpośredni dostęp do usług globalnych.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Użyj GetGlobalService

Czasami może być konieczne uzyskanie usługi z okna narzędzi lub kontenera kontroli, który nie został zlokalizowany, lub w innym systemie, który jest zlokalizowany przez dostawcę usług, który nie wie o żądaną usługę. Na przykład możesz chcieć zapisać w dzienniku aktywności z poziomu kontrolki. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [How to: Rozwiązywanie problemów z usługami](../../extensibility/how-to-troubleshoot-services.md).

Większość usług Visual Studio można uzyskać, wywołując metodę static <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> polega na zainicjowaniu dostawcy usługi w pamięci podręcznej, który został zainicjowany po raz pierwszy każdy pakietu VSPackage pochodzący z pakietu. Należy zastanowić się, że ten warunek jest spełniony lub został przygotowany dla usługi o wartości null.

Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> działa prawidłowo w większości czasu.

- Jeśli pakietu VSPackage zapewnia usługę znaną tylko innemu pakietu VSPackage, pakietu VSPackage żądający usługi jest zlokalizowana przed załadowaniem usługi pakietu VSPackage.

- Jeśli okno narzędzi jest tworzone przez pakietu VSPackage, pakietu VSPackage jest zlokalizowane przed utworzeniem okna narzędzi.

- Jeśli kontener formantów jest hostowany w oknie narzędzi utworzonym przez pakietu VSPackage, pakietu VSPackage jest zlokalizowane przed utworzeniem kontenera sterowania.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać usługę z poziomu okna narzędzi lub kontenera kontrolek

- Wstaw ten kod w konstruktorze, oknie narzędzi lub kontenerze formantów:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Ten kod uzyskuje usługę SVsActivityLog i rzutuje ją na interfejs IVsActivityLog, który może być używany do zapisywania w dzienniku aktywności. Aby zapoznać się z przykładem, zobacz [How to: Use the Activity Log](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Zobacz też

- [Lista dostępnych usług](../../extensibility/internals/list-of-available-services.md)
- [Korzystanie z usług i dostarczanie ich](../../extensibility/using-and-providing-services.md)
- [Rzutowanie i konwersje typów](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Rzutowanie](/cpp/cpp/casting)