---
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49e8f151aa01037a0bc18161fbe94a00488394db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953841"
---
# <a name="disassemblydata"></a>DisassemblyData
Opisuje jedną instrukcję demontażu dla zintegrowanego środowiska programistycznego (IDE) do wyświetlenia.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Stała [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) , która określa, które pola są wypełnione.

`bstrAddress`\
Adres jako przesunięcie od pewnego punktu początkowego (zazwyczaj początku skojarzonej funkcji).

`bstrCodeBytes`\
Bajty kodu dla tej instrukcji.

`bstrOpcode`\
Kod operacji dla tej instrukcji.

`bstrOperands`\
Operandy dla tej instrukcji.

`bstrSymbol`\
Nazwa symbolu (jeśli istnieje) skojarzona z adresem (symbol publiczny, etykieta itp.).

`uCodeLocationId`\
Identyfikator lokalizacji kodu dla tego rozbudowy wiersza. Jeśli adres kontekstu kodu z jednego wiersza jest większy niż adres kontekstu kodu innego, wówczas identyfikator lokalizacji kodu, który został rozłożony, będzie również większy niż identyfikator lokalizacji kodu drugiego.

`posBeg`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która odnosi się do pozycji w dokumencie, w której zaczynają się dane demontażu.

`posEnd`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która odnosi się do pozycji w dokumencie, w której kończą się dane demontażu.

`bstrDocumentUrl`\
W przypadku dokumentów tekstowych, które mogą być reprezentowane jako nazwy plików, `bstrDocumentUrl` pole jest wypełniane nazwą pliku, w którym można znaleźć źródło, przy użyciu formatu `file://file name` .

W przypadku dokumentów tekstowych, które nie mogą być reprezentowane jako nazwy plików, `bstrDocumentUrl` jest unikatowym identyfikatorem dla dokumentu, a aparat debugowania musi implementować metodę [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .

To pole może również zawierać dodatkowe informacje dotyczące sum kontrolnych. Aby uzyskać szczegółowe informacje, zobacz uwagi.

`dwByteOffset`\
Liczba bajtów instrukcji od początku wiersza kodu.

`dwFlags`\
Stała [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) , która określa, które flagi są aktywne.

## <a name="remarks"></a>Uwagi
Każda `DisassemblyData` Struktura opisuje jedną instrukcję odbudowy. Tablica tych struktur jest zwracana z metody [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) jest używana tylko do dokumentów tekstowych. Zakres kodu źródłowego dla tej instrukcji jest wypełniany tylko dla pierwszej instrukcji wygenerowanej na podstawie instrukcji lub wiersza, na przykład, kiedy `dwByteOffset == 0` .

W przypadku dokumentów, które nie są tekstowe, kontekst dokumentu można uzyskać z kodu, a `bstrDocumentUrl` pole powinno być wartością null. Jeśli `bstrDocumentUrl` pole jest takie samo jak `bstrDocumentUrl` pole w poprzednim `DisassemblyData` elemencie tablicy, a następnie ustaw `bstrDocumentUrl` wartość na null.

Jeśli `dwFlags` pole ma `DF_DOCUMENT_CHECKSUM` ustawioną flagę, dodatkowe informacje o sumie kontrolnej następuje po ciągu wskazanym przez `bstrDocumentUrl` pole. W odróżnieniu od terminatora ciągu o wartości null następuje identyfikator GUID identyfikujący algorytm sumy kontrolnej, po którym następuje 4-bajtowa wartość wskazująca liczbę bajtów w sumie kontrolnej, a po nim następuje licznik sum kontrolnych. Zobacz przykład w tym temacie, w jaki sposób kodować i dekodowanie tego pola w [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Przykład
`bstrDocumentUrl`Pole może zawierać dodatkowe informacje inne niż ciąg, jeśli `DF_DOCUMENT_CHECKSUM` flaga jest ustawiona. Proces tworzenia i odczytywania tego zakodowanego ciągu jest prosty w [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . Jednak w programie [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] jest to kolejna kwestia. Dla osób, które są chcesz wiedzieć, w poniższym przykładzie pokazano jeden ze sposobów tworzenia zakodowanego ciągu z [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] i jeden sposób dekodowanie zakodowanego ciągu w [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Przeczytaj](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
