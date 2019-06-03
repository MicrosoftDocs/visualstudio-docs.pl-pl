---
title: IManagedAddin — interfejs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 320b20fa40250ca47dd414b362059e152eba2c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420992"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin — interfejs
  Implementowanie imanagedaddin — interfejs do tworzenia składnika, który ładuje zarządzanych dodatków narzędzi VSTO. Ten interfejs został dodany w Microsoft Office system 2007.

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
 Poniższa tabela zawiera listę metod, które są definiowane przez imanagedaddin — interfejs.

|Nazwa|Opis|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Wywołuje się, gdy Microsoft Office ładowania aplikacji zarządzanych dodatku narzędzi VSTO.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Wywoływane tuż przed Microsoft Office aplikacji zwalnia zarządzane dodatku narzędzi VSTO.|

## <a name="remarks"></a>Uwagi
 Aplikacje Microsoft Office, począwszy od systemu Microsoft Office 2007, skorzystaj imanagedaddin — interfejs, aby załadować dodatków narzędzi VSTO dla pakietu Office. Możesz zaimplementować imanagedaddin — interfejs do tworzenia własnych dodatku narzędzi VSTO programu ładującego i środowisko uruchomieniowe dla zarządzanych dodatków narzędzi VSTO, zamiast korzystać z dodatku narzędzi VSTO programu ładującego (*VSTOLoader.dll*) i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Aby uzyskać więcej informacji, zobacz [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>W jaki sposób zarządzane dodatki są ładowane.
 Po uruchomieniu aplikacji, wykonywane są następujące kroki:

1. Aplikacja umożliwia odnalezienie dodatków narzędzi VSTO dla programów, wyszukując wpisy w następującym kluczu rejestru:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Każdy wpis w ramach tego klucza rejestru jest unikatowy identyfikator dodatku narzędzi VSTO. Zazwyczaj jest to nazwa zestawu dodatków narzędzi VSTO dla programów.

2. Aplikacja szuka `Manifest` wejścia we wpisie dla każdego dodatku narzędzi VSTO.

    Pełna ścieżka manifestu w mogą być przechowywane w zarządzanych dodatków narzędzi VSTO dla programów `Manifest` wpis w **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<Nazwa aplikacji >_ \Addins\\  _\<identyfikator dodatku >_ **. Manifestu to plik (zazwyczaj plik XML), który zawiera informacje, które są używane do ładowania dodatku narzędzi VSTO.

3. Jeśli aplikacja wykryje `Manifest` wpisu, aplikacja próbuje załadować zarządzanego dodatku narzędzi VSTO programu ładującego składnika. Aplikacja wykonuje to zadanie w trakcie tworzenia obiektów COM, który implementuje imanagedaddin — interfejs.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zawiera składnik modułu ładującego dodatku narzędzi VSTO (*VSTOLoader.dll*), lub możesz utworzyć własne, implementowanie imanagedaddin — interfejs.

4. Wywołania aplikacji [IManagedAddin::Load](../vsto/imanagedaddin-load.md) metody i przekazuje wartości `Manifest` wpisu.

5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) metoda wykonuje zadania wymagane do załadowania dodatku narzędzi VSTO dla programów, takich jak Konfigurowanie zasad aplikacji domen i zabezpieczeń dla dodatku narzędzi VSTO dla programów, który jest ładowany.

   Aby uzyskać więcej informacji na temat rejestru klucze, korzystających z aplikacji Microsoft Office wykrycie i załadowanie zarządzanych dodatków narzędzi VSTO dla programów, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Wskazówki dotyczące implementacji imanagedaddin —
 W przypadku zaimplementowania imanagedaddin — należy zarejestrować bibliotekę DLL, która zawiera implementację przy użyciu następujących CLSID:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Aplikacje Microsoft Office Użyj tego identyfikatora CLSID, aby utworzyć obiekt COM, który implementuje imanagedaddin —.

> [!CAUTION]
> Ten identyfikator CLSID jest również używany przez *VSTOLoader.dll* w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. W związku z tym, jeśli używasz imanagedaddin — do tworzenia własnych dodatku narzędzi VSTO programu ładującego i składnika środowiska uruchomieniowego, nie można wdrożyć składnika na komputerach, na których działają dodatków narzędzi VSTO dla programów, które zależą od [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="see-also"></a>Zobacz także
- [Niezarządzany wykaz interfejsów API &#40;programowanie Office w Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
