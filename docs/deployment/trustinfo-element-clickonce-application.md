---
title: '&lt;trustInfo, &gt; element (Aplikacja ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5873eb18b2f803acfd5aba9444657884b1a24581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184435"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo, &gt; element (Aplikacja ClickOnce)
Opisuje minimalne uprawnienia zabezpieczeń wymagane do uruchomienia aplikacji na komputerze klienckim.

## <a name="syntax"></a>Składnia

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `trustInfo`Element jest wymagany i znajduje się w `asm.v2` przestrzeni nazw. Nie ma atrybutów i zawiera następujące elementy.

## <a name="security"></a>security
 Wymagany. Ten element jest elementem podrzędnym `trustInfo` elementu. Zawiera `applicationRequestMinimum` element i nie ma żadnych atrybutów.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 Wymagany. Ten element jest elementem podrzędnym `security` elementu i zawiera `PermissionSet` `assemblyRequest` elementy,, i `defaultAssemblyRequest` . Ten element nie ma atrybutów.

## <a name="permissionset"></a>PermissionSet
 Wymagany. Ten element jest elementem podrzędnym `applicationRequestMinimum` elementu i zawiera `IPermission` element. Ten element ma następujące atrybuty.

- `ID`

     Wymagany. Identyfikuje zestaw uprawnień. Ten atrybut może mieć dowolną wartość. Identyfikator jest przywoływany w `defaultAssemblyRequest` `assemblyRequest` atrybutach i.

- `version`

     Wymagany. Identyfikuje wersję uprawnienia. Zwykle ta wartość jest `1` .

## <a name="ipermission"></a>IPermission
 Opcjonalny. Ten element jest elementem podrzędnym `PermissionSet` elementu. `IPermission`Element w pełni identyfikuje klasę uprawnień w .NET Framework. `IPermission`Element ma następujące atrybuty, ale może mieć dodatkowe atrybuty odpowiadające właściwościom klasy uprawnień. Aby dowiedzieć się, jaka jest składnia określonego uprawnienia, zobacz przykłady wymienione w pliku Security.config.

- `class`

     Wymagany. Identyfikuje klasę uprawnień przez silną nazwę. Na przykład poniższy kod identyfikuje `FileDialogPermission` Typ.

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     Wymagany. Identyfikuje wersję uprawnienia. Zazwyczaj ta wartość jest `1` .

- `Unrestricted`

     Wymagany. Określa, czy aplikacja wymaga nieograniczonych uprawnień. Jeśli `true` , przyznanie uprawnienia jest bezwarunkowe. Jeśli `false` , lub jeśli ten atrybut jest niezdefiniowany, jest ograniczony zgodnie z atrybutami specyficznymi dla uprawnień zdefiniowanymi w `IPermission` tagu. Wykonaj następujące uprawnienia:

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     W tym przykładzie deklaracja dla <xref:System.Security.Permissions.EnvironmentPermission> ogranicza aplikację do odczytu tylko zmiennej środowiskowej username, podczas gdy deklaracja dla <xref:System.Security.Permissions.FileDialogPermission> daje aplikacji nieograniczone użycie wszystkich <xref:System.Windows.Forms.FileDialog> klas.

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 Opcjonalny. Identyfikuje zestaw uprawnień przyznanych dla wszystkich zestawów. Ten element jest elementem podrzędnym `applicationRequestMinimum` elementu i ma następujący atrybut.

- `permissionSetReference`

     Wymagany. Identyfikuje identyfikator zestawu uprawnień, który jest uprawnieniem domyślnym. Zestaw uprawnień jest zadeklarowany w `PermissionSet` elemencie.

## <a name="assemblyrequest"></a>assemblyRequest
 Opcjonalny. Identyfikuje uprawnienia do określonego zestawu. Ten element jest elementem podrzędnym `applicationRequestMinimum` elementu i ma następujące atrybuty.

- `Name`

     Wymagany. Identyfikuje nazwę zestawu.

- `permissionSetReference`

     Wymagany. Identyfikuje identyfikator zestawu uprawnień wymaganego przez ten zestaw. Zestaw uprawnień jest zadeklarowany w `PermissionSet` elemencie.

## <a name="requestedprivileges"></a>requestedPrivileges
 Opcjonalny. Ten element jest elementem podrzędnym `security` elementu i zawiera `requestedExecutionLevel` element. Ten element nie ma atrybutów.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 Opcjonalny. Identyfikuje poziom zabezpieczeń, na którym aplikacja żąda wykonania. Ten element nie ma elementów podrzędnych i ma następujące atrybuty.

- `Level`

   Wymagany. Wskazuje poziom zabezpieczeń żądania aplikacji. Możliwe wartości:

   `asInvoker`, żądanie braku dodatkowych uprawnień. Na tym poziomie nie są wymagane żadne dodatkowe komunikaty zaufania.

   `highestAvailable`, żądanie najwyższych uprawnień dostępnych dla procesu nadrzędnego.

   `requireAdministrator`, żądanie pełnych uprawnień administratora.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje będą instalowane tylko z wartością `asInvoker` . Instalowanie z jakąkolwiek inną wartością zakończy się niepowodzeniem.

- `uiAccess`

   Opcjonalny. Wskazuje, czy aplikacja wymaga dostępu do elementów chronionego interfejsu użytkownika. Wartości to `true` lub `false` , a wartość domyślna to false. Tylko podpisane aplikacje powinny mieć wartość true.

## <a name="remarks"></a>Uwagi
 Jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja prosi o więcej uprawnień niż komputer kliencki zostanie domyślnie udzielony, Menedżer zaufania środowiska uruchomieniowego języka wspólnego będzie monitować użytkownika, jeśli chce udzielić aplikacji tego poziomu zaufania. Jeśli to się nie powiedzie, aplikacja nie zostanie uruchomiona; w przeciwnym razie zostanie uruchomiony z żądanymi uprawnieniami.

 Wszystkie uprawnienia wymagane przy użyciu `defaultAssemblyRequest` i `assemblyRequest` zostaną przyznane bez monitowania użytkownika, Jeśli manifest wdrożenia ma prawidłową licencję zaufania.

 Aby uzyskać więcej informacji na temat podniesienia uprawnień, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md). Aby uzyskać więcej informacji na temat wdrażania zasad, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

## <a name="examples"></a>Przykłady
 Poniższe trzy przykłady kodu ilustrują `trustInfo` elementy dla domyślnych nazwanych stref zabezpieczeń — Internet, LocalIntranet i FullTrust — do użycia w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeście aplikacji wdrożenia.

 Pierwszy przykład ilustruje `trustInfo` element dla domyślnych uprawnień dostępnych w strefie zabezpieczeń internetowych.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 Drugi przykład ilustruje `trustInfo` element dla domyślnych uprawnień dostępnych w strefie zabezpieczeń LocalIntranet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 Trzeci przykład ilustruje `trustInfo` element dla domyślnych uprawnień dostępnych w strefie zabezpieczeń FullTrust.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>Zobacz też
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)