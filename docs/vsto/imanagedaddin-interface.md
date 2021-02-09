---
title: IManagedAddin — interfejs
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89e705296c6051b8bdec823e523f0a386ff7ff76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920437"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin — interfejs
  Zaimplementuj interfejs IManagedAddin —, aby utworzyć składnik ładujący zarządzane dodatki narzędzi VSTO. Ten interfejs został dodany w systemie Microsoft Office 2007.

## <a name="syntax"></a>Składnia

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>Metody
 W poniższej tabeli wymieniono metody, które są zdefiniowane przez interfejs IManagedAddin —.

|Nazwa|Opis|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wywoływana, gdy aplikacja Microsoft Office ładuje dodatek zarządzanego narzędzia VSTO.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wywoływana tuż przed załadowaniem przez aplikację Microsoft Office zarządzanego dodatku VSTO.|

## <a name="remarks"></a>Uwagi
 Microsoft Office aplikacji, począwszy od systemu Microsoft Office 2007, użyj interfejsu IManagedAddin —, aby ułatwić ładowanie dodatków pakietu Office VSTO. Można zaimplementować interfejs IManagedAddin —, aby utworzyć własny moduł ładujący i środowisko uruchomieniowe programu VSTO dla zarządzanych dodatków narzędzi VSTO, zamiast korzystać z modułu ładującego dodatku VSTO (*VSTOLoader.dll*) i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Aby uzyskać więcej informacji, zobacz [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Jak są ładowane zarządzane Dodatki
 Po uruchomieniu aplikacji wystąpią następujące czynności:

1. Aplikacja odnajduje Dodatki programu VSTO, szukając wpisów w następującym kluczu rejestru:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Każdy wpis w tym kluczu rejestru jest unikatowym IDENTYFIKATORem dodatku VSTO. Zazwyczaj jest to nazwa zestawu dodatku VSTO.

2. Aplikacja szuka `Manifest` wpisu dla każdego dodatku VSTO.

    Zarządzane dodatki narzędzi VSTO mogą przechowywać pełną ścieżkę manifestu w `Manifest` wpisie w obszarze **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_**. Manifest to plik (zazwyczaj plik XML), który zawiera informacje, które są używane do załadowania dodatku VSTO.

3. Jeśli aplikacja znajdzie `Manifest` wpis, aplikacja podejmie próbę załadowania zarządzanego składnika modułu ładującego programu VSTO. W tym celu aplikacja podejmuje próbę utworzenia obiektu COM, który implementuje interfejs IManagedAddin —.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zawiera składnik modułu ładującego dodatku VSTO (*VSTOLoader.dll*) lub można utworzyć własny przez implementację interfejsu IManagedAddin —.

4. Aplikacja wywołuje metodę [IManagedAddin —:: Load](../vsto/imanagedaddin-load.md) i przekazuje wartość `Manifest` wpisu.

5. Metoda [IManagedAddin —:: Load](../vsto/imanagedaddin-load.md) wykonuje zadania wymagane do załadowania dodatku VSTO, takie jak konfigurowanie domeny aplikacji i zasad zabezpieczeń dla załadowanego dodatku VSTO.

   Aby uzyskać więcej informacji na temat kluczy rejestru, które Microsoft Office aplikacje używają do odnajdywania i ładowania dodatków zarządzanego narzędzia VSTO, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Wskazówki dotyczące wdrażania IManagedAddin —
 W przypadku zaimplementowania IManagedAddin — należy zarejestrować bibliotekę DLL, która zawiera implementację, przy użyciu następującego identyfikatora CLSID:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Aplikacje Microsoft Office używają tego identyfikatora CLSID do tworzenia obiektu COM, który implementuje IManagedAddin —.

> [!CAUTION]
> Ten identyfikator CLSID jest również używany przez *VSTOLoader.dll* w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . W związku z tym, jeśli używasz IManagedAddin — do tworzenia własnego modułu ładującego dodatek narzędzi VSTO i składnika środowiska uruchomieniowego, nie możesz wdrożyć składnika na komputerach z uruchomionymi dodatkami VSTO, które korzystają z programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Zobacz też
- [Niezarządzana dokumentacja interfejsu API &#40;Office Development w programie Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
