#/
# @license Apache-2.0
#
# Copyright (c) 2017 The Stdlib Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#/

# DEPENDENCIES #

ifeq ($(MARKDOWN_LINTER), remark)
	include $(TOOLS_MAKE_LIB_DIR)/lint/markdown/remark.mk
endif


# RULES #

# Lint.
#
# This target lints all Markdown files.

lint-markdown: $(NODE_MODULES)
ifeq ($(FAIL_FAST), true)
	$(QUIET) $(FIND_MARKDOWN_CMD) | grep '^[\/]\|^[a-zA-Z]:[/\]' | while read -r file; do \
		echo ''; \
		echo "Linting file: $$file"; \
		$(MARKDOWN_LINT) $(MARKDOWN_LINT_FLAGS) $$file || exit 1; \
	done
else
	$(QUIET) $(FIND_MARKDOWN_CMD) | grep '^[\/]\|^[a-zA-Z]:[/\]' | while read -r file; do \
		echo ''; \
		echo "Linting file: $$file"; \
		$(MARKDOWN_LINT) $(MARKDOWN_LINT_FLAGS) $$file || echo 'Linting failed.'; \
	done
endif

.PHONY: lint-markdown


# Lint.
#
# This target lints Markdown files according to a specified file list. Note that we expect `$FILES` to be a Markdown file list.

lint-markdown-files: $(NODE_MODULES)
ifeq ($(FAIL_FAST), true)
	$(QUIET) for file in $(FILES); do \
		echo ''; \
		echo "Linting file: $$file"; \
		$(MARKDOWN_LINT) $(MARKDOWN_LINT_FLAGS) $$file || exit 1; \
	done
else
	$(QUIET) for file in $(FILES); do \
		echo ''; \
		echo "Linting file: $$file"; \
		$(MARKDOWN_LINT) $(MARKDOWN_LINT_FLAGS) $$file || echo 'Linting failed.'; \
	done
endif

.PHONY: lint-markdown-files
