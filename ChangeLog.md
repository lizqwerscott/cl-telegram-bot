<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-40CHANGELOG-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

# ChangeLog

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E5-2E0-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.5.0 (2024-02-18)

<a id="added"></a>

### Added

* Now bot can be started in debug mode. When this mode is on, then interactive debugger will pop up on errors.
* If bot defines some commands implementing [`cl-telegram-bot/entities/command:on-command`][56c0] generic-function, then
  these commands will be reported to the telegram server automatically and it will show the to user when he
  starts text with `/`.
* Added support for buttons with callbacks. To define a callback, implement a method for
  [`cl-telegram-bot/callback:on-callback`][1b93] generic-function. After that, you can construct an inline keyboard
  using [`cl-telegram-bot/inline-keyboard:inline-keyboard`][35e0] function and [`cl-telegram-bot/inline-keyboard:callback-button`][734b] function.
  This keyboard object can be supplied as `:REPLY-MARKUP` argument to [`cl-telegram-bot/response:reply`][0d9a] function.
* New functions `cl-telegram-bot/response:alert` ([`1`][61ac] [`2`][4b97]) and `cl-telegram-bot/response:notify` ([`1`][6672] [`2`][0817]) were added. An example usage of these functions
  along with inline keyboard was added to `example/bot.lisp`.
* Function [`cl-telegram-bot/response-processing:interrupt-processing`][e96a] was added in case if you want to interrupt processing of
  current message and skip the rest of the handler.
* Function [`cl-telegram-bot/message:get-current-message`][4af2] was added.
* Function [`cl-telegram-bot/message:get-current-chat`][e428] was added.

<a id="removed"></a>

### Removed

* Function `CL-TELEGRAM-BOT/MESSAGE:REPLY` was removed and replaced with [`cl-telegram-bot/response:reply`][0d9a] function.
  Previously it interrupted the processing flow and you only was able to reply once. With the new function
  you can respond with different pieces, for example to show user a image and text with inline keyboard.

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E4-2E0-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.4.0 (2023-04-22)

* Changed a lot of imports some symbols not bound to functions were removed, some readers and accessors are exported.
* Added an autogenerated `API` reference.

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E3-2E2-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.3.2 (2022-07-10)

* Change the parameters of `make-request` to allow passing request parameters straight into it.
* Add `id` slot to `message`; add `forward-message`, `delete-message` functions reliant on `id`.
* Add more `message` types: `reply`, `video-message`, `document-message` and other media message types.
* Add `send-*` media-sending message types.
* Add more `chat` types: `group`, `supergroup`, and `channel`.

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E3-2E1-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.3.1 (2020-01-04)

* Fixed work with latest `dexador`, because it does not accept `:stream t` anymore.

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E3-2E0-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.3.0 (2019-09-22)

* Bot was fixed to use latest Dexador with support
  of `read-timeout` and `connect-timeout`.

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E2-2E0-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.2.0 (2019-09-16)

* Added a dependency from `trivial-timeout` and now connect timeout is used when
  doing requests to `API`.
* Function `make-<bot-class>` now proxie any parameters to the class's constructor.
* Now function `stop-processing` checks if thread is alive before destroying it.

<a id="x-28CL-TELEGRAM-BOT-DOCS-2FCHANGELOG-3A-3A-7C0-2E1-2E0-7C-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## 0.1.0 (2018-09-17)

<a id="refactorings"></a>

### Refactorings

Project was broken down to subpackages, nicknames `telegram-bot` and
`tg-bot` were removed, because now system uses `ASDF`'s
package-inferred-system class and each file have it's own separate packages.


[1b93]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FCALLBACK-3AON-CALLBACK-20GENERIC-FUNCTION-29
[56c0]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FENTITIES-2FCOMMAND-3AON-COMMAND-20GENERIC-FUNCTION-29
[734b]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FINLINE-KEYBOARD-3ACALLBACK-BUTTON-20FUNCTION-29
[35e0]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FINLINE-KEYBOARD-3AINLINE-KEYBOARD-20FUNCTION-29
[e428]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FMESSAGE-3AGET-CURRENT-CHAT-20FUNCTION-29
[4af2]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FMESSAGE-3AGET-CURRENT-MESSAGE-20FUNCTION-29
[4b97]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FRESPONSE-3AALERT-20CLASS-29
[61ac]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FRESPONSE-3AALERT-20FUNCTION-29
[0817]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FRESPONSE-3ANOTIFY-20CLASS-29
[6672]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FRESPONSE-3ANOTIFY-20FUNCTION-29
[0d9a]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FRESPONSE-3AREPLY-20FUNCTION-29
[e96a]: https://40ants.com/cl-telegram-bot/#x-28CL-TELEGRAM-BOT-2FRESPONSE-PROCESSING-3AINTERRUPT-PROCESSING-20FUNCTION-29

* * *
###### [generated by [40ANTS-DOC](https://40ants.com/doc/)]
