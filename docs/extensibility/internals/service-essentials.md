---
title: Podstawowe usługi | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303240"
---
# <a name="service-essentials"></a>Podstawowe informacje o usłudze
Usługa jest umową między dwoma vspackages. Jeden VSPackage zawiera określony zestaw interfejsów dla innego VSPackage do wykorzystania. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sama kolekcja VSPackages, który świadczy usługi dla innych VSPackages.

 Na przykład można użyć usługi SVsActivityLog w celu uzyskania interfejsu IVsActivityLog, którego można użyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zapewnia również niektóre wbudowane usługi, które nie są zarejestrowane. VsPackages można zastąpić wbudowane lub inne usługi, zapewniając zastąpienie usługi. Tylko jedno zastąpienie usługi jest dozwolone dla każdej usługi.

 Usługi nie mają możliwości wykrycia. W związku z tym należy znać identyfikator usługi (SID) usługi, które mają być używane i musisz wiedzieć, które interfejsy zapewnia. Dokumentacja referencyjna dla usługi zawiera te informacje.

- Pakiety VSPackages, które świadczą usługi są nazywane dostawcami usług.

- Usługi, które są dostarczane do innych vspackages są nazywane usług globalnych.

- Usługi, które są dostępne tylko dla VSPackage, który implementuje je lub do dowolnego obiektu, który tworzy, są nazywane usług lokalnych.

- Usługi, które zastępują wbudowane usługi lub usługi świadczone przez inne pakiety, są nazywane zastąpieniami usług.

- Usługi lub zastąpienia usług są ładowane na żądanie, oznacza to, że dostawca usług jest ładowany, gdy usługa, którą zapewnia, jest żądana przez inny program VSPackage.

- Aby obsługiwać ładowanie na żądanie, usługodawca rejestruje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]swoje globalne usługi za pomocą . Aby uzyskać więcej informacji, zobacz [Jak: Świadczenie usługi](../../extensibility/how-to-provide-a-service.md).

- Po uzyskaniu usługi użyj [QueryInterface](/cpp/atl/queryinterface) (kod niezarządzany) lub rzutowania (kod zarządzany), aby uzyskać żądany interfejs, na przykład:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Kod zarządzany odwołuje się do usługi według jej typu, podczas gdy kod niezarządzany odwołuje się do usługi przez jego identyfikator GUID.

- Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładowania VSPackage, przekazuje dostawcy usług do VSPackage dać VSPackage dostęp do usług globalnych. Jest to określane jako "siting" VSPackage.

- VSPackages mogą być dostawcami usług dla obiektów, które tworzą. Na przykład formularz może wysłać żądanie usługi kolorów do ramki, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]które może przekazać żądanie do .

- Obiekty zarządzane, które są głęboko zagnieżdżone <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> lub w ogóle nie są umiejscowione, mogą wymagać bezpośredniego dostępu do usług globalnych.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Korzystanie z usługi GetGlobalService

Czasami może być konieczne uzyskanie usługi z okna narzędzia lub kontenera formantu, który nie został umiejscowiony, lub został umiejscowiony u dostawcy usług, który nie wie o żądanej usłudze. Na przykład można zapisać w dzienniku aktywności z poziomu formantu. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [Jak: Rozwiązywanie problemów z usługami](../../extensibility/how-to-troubleshoot-services.md).

Większość usług programu Visual Studio można <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> uzyskać, wywołując metodę statyczną.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>opiera się na buforowanym dostawcy usług, który jest inicjowany po raz pierwszy wszystkie VSPackage pochodzące z pakietu jest zlokalizowany. Należy zagwarantować, że ten warunek jest spełniony, w przeciwnym razie być przygotowanym do usługi null.

Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> działa poprawnie przez większość czasu.

- Jeśli VSPackage udostępnia usługę znaną tylko innemu pakietowi VSPackage, usługa VSPackage, która żąda usługi, jest obsługiwana przed załadowaniem usługi vspackage.

- Jeśli okno narzędzia jest tworzony przez VSPackage, VSPackage jest umiejscowiona przed utworzeniem okna narzędzia.

- Jeśli kontener formantu jest obsługiwany przez okno narzędzia utworzone przez VSPackage, VSPackage jest umiejscowiony przed utworzeniem kontenera formantu.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać usługę z okna narzędzia lub kontenera sterującego

- Wstaw ten kod w konstruktorze, oknie narzędzia lub kontenerze formantu:

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

    Ten kod uzyskuje usługę SVsActivityLog i rzuca go do interfejsu IVsActivityLog, który może służyć do zapisu w dzienniku aktywności. Na przykład zobacz [Jak: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Zobacz też

- [Lista dostępnych usług](../../extensibility/internals/list-of-available-services.md)
- [Korzystanie z usług i dostarczanie ich](../../extensibility/using-and-providing-services.md)
- [Rzutowanie i konwersje typów](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Rzutowanie](/cpp/cpp/casting)