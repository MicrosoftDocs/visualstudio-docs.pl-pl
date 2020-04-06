---
title: 'Jak: Rozwiązywanie problemów z usługami | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710747"
---
# <a name="how-to-troubleshoot-services"></a>Jak: Rozwiązywanie problemów z usługami
Istnieje kilka typowych problemów, które mogą wystąpić podczas próby uzyskania usługi:

- Usługa nie jest [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zarejestrowana w .

- Usługa jest żądana przez typ interfejsu, a nie według typu usługi.

- VsPackage żądanie usługi nie został umiejscowiony.

- Używany jest niewłaściwy dostawca usług.

  Jeśli nie można uzyskać żądanej usługi, wywołanie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zwraca wartość null. Zawsze należy przetestować pod kątem wartości null po zażądaniu usługi:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Aby rozwiązać problem z usługą

1. Sprawdź rejestr systemowy, aby sprawdzić, czy usługa została poprawnie zarejestrowana. Aby uzyskać więcej informacji, zobacz [Jak: Świadczenie usługi](../extensibility/how-to-provide-a-service.md).

    Poniższy fragment pliku *reg* pokazuje, jak usługa SVsTextManager może być zarejestrowana:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    W powyższym przykładzie numer wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]jest wersją , taką jak 12.0 lub 14.0, kluczem {F5E7E71D-1401-11d1-883B-0000F87579D2} jest identyfikatorem usługi (SID) usługi, SVsTextManager i wartość domyślna {F5E7E720-1401-11d1-883B-0000F87579D2} to identyfikator GUID pakietu menedżera tekstu VSPackage, który zapewnia usługę.

2. Użyj typu usługi, a nie typu interfejsu podczas wywoływania GetService. Podczas żądania usługi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]z <xref:Microsoft.VisualStudio.Shell.Package> , wyodrębnia identyfikator GUID z typu. Usługa nie zostanie znaleziona, jeśli istnieją następujące warunki:

   1. Typ interfejsu jest przekazywany do GetService zamiast typu usługi.

   2. Żaden identyfikator GUID nie jest jawnie przypisany do interfejsu. W związku z tym system tworzy domyślny identyfikator GUID dla obiektu w razie potrzeby.

3. Upewnij się, że usługa VSPackage żądająca usługi została umiejscowiona. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]witryn VSPackage po skonstruowaniu go <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>i przed wywołaniem .

    Jeśli masz kod w konstruktorze VSPackage, który `Initialize` wymaga usługi, przenieś go do metody.

4. Upewnij się, że korzystasz z właściwego dostawcy usług.

    Nie wszyscy usługodawcy są podobni. Dostawca usług, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który przekazuje do okna narzędzia różni się od tego, który przechodzi do VSPackage. Dostawca usług okna narzędzia <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>wie o , <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>ale nie wie o . Można wywołać, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> aby uzyskać dostawcę usług VSPackage z poziomu okna narzędzia.

    Jeśli okno narzędzia obsługuje formant użytkownika lub inny kontener formantu, kontener zostanie umiejscowiona [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przez model składnika systemu Windows i nie będzie miał dostępu do żadnych usług. Można wywołać, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> aby uzyskać dostawcę usług VSPackage z wewnątrz kontenera kontroli.

## <a name="see-also"></a>Zobacz też
- [Lista dostępnych usług](../extensibility/internals/list-of-available-services.md)
- [Korzystanie i świadczenie usług](../extensibility/using-and-providing-services.md)
- [Podstawowe usługi](../extensibility/internals/service-essentials.md)
