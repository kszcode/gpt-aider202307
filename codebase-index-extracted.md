Configuration: {'root_dir': '/Users/km1/2code/experiments/gpt-aider202307/.', 'file_extensions': ['py', 'js', 'ts', 'go', 'html']}
# Code Structure Documentation

## File: setup.py

## File: benchmark/benchmark.py
### Functions
- show_stats(dirnames, graphs)
- plot_timing(df)
- plot_outcomes(df, repeats, repeat_hi, repeat_lo, repeat_avg)
- resolve_dirname(dirname, use_single_prior, make_new)
- main(dirnames, graphs, model, edit_format, keywords, clean, cont, make_new, no_unit_tests, no_aider, verbose, stats_only, diffs_only, tries, threads, num_tests)
- show_diffs(dirnames)
- load_results(dirname)
- summarize_results(dirname)
- run_test(testdir, model_name, edit_format, tries, no_unit_tests, no_aider, verbose, commit_hash)
- run_unit_tests(testdir, history_fname)
- cleanup_test_output(output, testdir)

## File: benchmark/rungrid.py
### Functions
- main()
- run(dirname, model, edit_format)

## File: benchmark/prompts.py

## File: benchmark/test_benchmark.py
### Class: TestCleanupTestOutput
- test_cleanup_test_output(self)
- test_cleanup_test_output_lines(self)

## File: aider/repomap.py
### Class: RepoMap
- __init__(self, map_tokens, root, main_model, io, repo_content_prefix, verbose)
- get_repo_map(self, chat_files, other_files)
- token_count(self, string)
- get_rel_fname(self, fname)
- split_path(self, path)
- load_tags_cache(self)
- save_tags_cache(self)
- get_mtime(self, fname)
- get_tags(self, fname, rel_fname)
- get_tags_raw(self, fname, rel_fname)
- get_ranked_tags(self, chat_fnames, other_fnames)
- get_ranked_tags_map(self, chat_fnames, other_fnames)
- to_tree(self, tags, chat_rel_fnames)
### Functions
- find_src_files(directory)
- get_random_color()

## File: aider/versioncheck.py
### Functions
- check_version(print_cmd)

## File: aider/sendchat.py
### Functions
- send_with_retries(model_name, messages, functions, stream)
- simple_send_with_retries(model_name, messages)

## File: aider/io.py
### Class: AutoCompleter
- __init__(self, root, rel_fnames, addable_rel_fnames, commands, encoding)
- get_completions(self, document, complete_event)
### Class: InputOutput
- __init__(self, pretty, yes, input_history_file, chat_history_file, input, output, user_input_color, tool_output_color, tool_error_color, encoding, dry_run)
- read_text(self, filename)
- write_text(self, filename, content)
- get_input(self, root, rel_fnames, addable_rel_fnames, commands)
- add_to_input_history(self, inp)
- get_input_history(self)
- user_input(self, inp, log_only)
- ai_output(self, content)
- confirm_ask(self, question, default)
- prompt_ask(self, question, default)
- tool_error(self, message)
- tool_output(self)
- append_chat_history(self, text, linebreak, blockquote)
### Functions
- _(event)

## File: aider/__init__.py

## File: aider/diffs.py
### Functions
- main()
- create_progress_bar(percentage)
- assert_newlines(lines)
- diff_partial_update(lines_orig, lines_updated, final, fname)
- find_last_non_deleted(lines_orig, lines_updated)

## File: aider/prompts.py

## File: aider/dump.py
### Functions
- cvt(s)
- dump()

## File: aider/voice.py
### Class: SoundDeviceError
### Class: Voice
- __init__(self)
- callback(self, indata, frames, time, status)
- get_prompt(self)
- record_and_transcribe(self, history, language)
- raw_record_and_transcribe(self, history, language)

## File: aider/utils.py
### Functions
- safe_abs_path(res)
- show_messages(messages, title, functions)

## File: aider/repo.py
### Class: GitRepo
- __init__(self, io, fnames, git_dname, aider_ignore_file)
- commit(self, fnames, context, prefix, message)
- get_rel_repo_dir(self)
- get_commit_message(self, diffs, context)
- get_diffs(self, fnames)
- diff_commits(self, pretty, from_commit, to_commit)
- get_tracked_files(self)
- filter_ignored_files(self, fnames)
- path_in_repo(self, path)
- abs_root_path(self, path)
- is_dirty(self, path)

## File: aider/main.py
### Functions
- get_git_root()
- guessed_wrong_repo(io, git_root, fnames, git_dname)
- setup_git(git_root, io)
- check_gitignore(git_root, io, ask)
- main(argv, input, output, force_git_root)
- scrub_sensitive_info(text)

## File: aider/commands.py
### Class: Commands
- __init__(self, io, coder, voice_language)
- is_command(self, inp)
- get_commands(self)
- get_command_completions(self, cmd_name, partial)
- do_run(self, cmd_name, args)
- matching_commands(self, inp)
- run(self, inp)
- cmd_commit(self, args)
- cmd_clear(self, args)
- cmd_tokens(self, args)
- cmd_undo(self, args)
- cmd_diff(self, args)
- completions_add(self, partial)
- glob_filtered_to_repo(self, pattern)
- cmd_add(self, args)
- completions_drop(self, partial)
- cmd_drop(self, args)
- cmd_git(self, args)
- cmd_run(self, args)
- cmd_exit(self, args)
- cmd_ls(self, args)
- cmd_help(self, args)
- cmd_voice(self, args)
### Functions
- expand_subdir(file_path)
- parse_quoted_filenames(args)
- fmt(v)

## File: aider/history.py
### Class: ChatSummary
- __init__(self, model, max_tokens)
- too_big(self, messages)
- tokenize(self, messages)
- summarize(self, messages, depth)
- summarize_all(self, messages)
### Functions
- main()

## File: aider/coders/single_wholefile_func_coder.py
### Class: SingleWholeFileFunctionCoder
- __init__(self)
- update_cur_messages(self, edited)
- render_incremental_response(self, final)
- live_diffs(self, fname, content, final)
- _update_files(self)

## File: aider/coders/wholefile_func_prompts.py
### Class: WholeFileFunctionPrompts

## File: aider/coders/single_wholefile_func_prompts.py
### Class: SingleWholeFileFunctionPrompts

## File: aider/coders/wholefile_func_coder.py
### Class: WholeFileFunctionCoder
- __init__(self)
- update_cur_messages(self, edited)
- render_incremental_response(self, final)
- live_diffs(self, fname, content, final)
- _update_files(self)

## File: aider/coders/__init__.py

## File: aider/coders/editblock_func_prompts.py
### Class: EditBlockFunctionPrompts

## File: aider/coders/wholefile_coder.py
### Class: WholeFileCoder
- __init__(self)
- update_cur_messages(self, edited)
- render_incremental_response(self, final)
- get_edits(self, mode)
- apply_edits(self, edits)
- do_live_diff(self, full_path, new_lines, final)

## File: aider/coders/base_coder.py
### Class: MissingAPIKeyError
### Class: ExhaustedContextWindow
### Class: Coder
- create(self, main_model, edit_format, io, skip_model_availabily_check)
- __init__(self, main_model, io, fnames, git_dname, pretty, show_diffs, auto_commits, dirty_commits, dry_run, map_tokens, verbose, assistant_output_color, code_theme, stream, use_git, voice_language, aider_ignore_file)
- find_common_root(self)
- add_rel_fname(self, rel_fname)
- abs_root_path(self, path)
- show_pretty(self)
- get_abs_fnames_content(self)
- choose_fence(self)
- get_files_content(self, fnames)
- get_repo_map(self)
- get_files_messages(self)
- run(self, with_message)
- keyboard_interrupt(self)
- summarize_start(self)
- summarize_worker(self)
- summarize_end(self)
- move_back_cur_messages(self, message)
- run_loop(self)
- fmt_system_prompt(self, prompt)
- format_messages(self)
- send_new_user_message(self, inp)
- update_cur_messages(self, edited)
- check_for_file_mentions(self, content)
- send(self, messages, model, functions)
- show_send_output(self, completion)
- show_send_output_stream(self, completion)
- live_incremental_response(self, live, final)
- render_incremental_response(self, final)
- get_rel_fname(self, fname)
- get_inchat_relative_files(self)
- get_all_relative_files(self)
- get_all_abs_files(self)
- get_last_modified(self)
- get_addable_relative_files(self)
- check_for_dirty_commit(self, path)
- allowed_to_edit(self, path)
- prepare_to_edit(self, edits)
- update_files(self)
- apply_updates(self)
- parse_partial_args(self)
- get_context_from_history(self, history)
- auto_commit(self, edited)
- dirty_commit(self)
### Functions
- wrap_fence(name)
- check_model_availability(io, main_model)

## File: aider/coders/wholefile_prompts.py
### Class: WholeFilePrompts

## File: aider/coders/editblock_func_coder.py
### Class: EditBlockFunctionCoder
- __init__(self, code_format)
- render_incremental_response(self, final)
- _update_files(self)
### Functions
- get_arg(edit, arg)

## File: aider/coders/base_prompts.py
### Class: CoderPrompts

## File: aider/coders/editblock_prompts.py
### Class: EditBlockPrompts

## File: aider/coders/editblock_coder.py
### Class: EditBlockCoder
- __init__(self)
- get_edits(self)
- apply_edits(self, edits)
### Functions
- prep(content)
- perfect_or_whitespace(whole_lines, part_lines, replace_lines)
- perfect_replace(whole_lines, part_lines, replace_lines)
- replace_most_similar_chunk(whole, part, replace)
- try_dotdotdots(whole, part, replace)
- replace_part_with_missing_leading_whitespace(whole_lines, part_lines, replace_lines)
- match_but_for_leading_whitespace(whole_lines, part_lines)
- replace_closest_edit_distance(whole_lines, part, part_lines, replace_lines)
- strip_quoted_wrapping(res, fname, fence)
- do_replace(fname, content, before_text, after_text, fence)
- strip_filename(filename, fence)
- find_original_update_blocks(content, fence)

## File: aider/models/openrouter.py
### Class: OpenRouterModel
- __init__(self, name)
### Functions
- edit_format_for_model(name)

## File: aider/models/__init__.py

## File: aider/models/model.py
### Class: Model
- create(cls, name)
- __str__(self)
- strong_model()
- weak_model()
- commit_message_models()
- token_count(self, messages)

## File: aider/models/openai.py
### Class: OpenAIModel
- __init__(self, name)
- is_gpt4(self)
- is_gpt35(self)

## File: tests/test_repomap.py
### Class: TestRepoMap
- test_get_repo_map(self)
- test_get_repo_map_with_identifiers(self)
- test_get_repo_map_all_files(self)
- test_get_repo_map_excludes_added_files(self)

## File: tests/test_editblock.py
### Class: TestUtils
- setUp(self)
- tearDown(self)
- __test_replace_most_similar_chunk(self)
- __test_replace_most_similar_chunk_not_perfect_match(self)
- test_strip_quoted_wrapping(self)
- test_strip_quoted_wrapping_no_filename(self)
- test_strip_quoted_wrapping_no_wrapping(self)
- test_find_original_update_blocks(self)
- test_find_original_update_blocks_mangled_filename_w_source_tag(self)
- test_find_original_update_blocks_quote_below_filename(self)
- test_find_original_update_blocks_unclosed(self)
- test_find_original_update_blocks_missing_filename(self)
- test_find_original_update_blocks_no_final_newline(self)
- test_incomplete_edit_block_missing_filename(self)
- test_replace_part_with_missing_varied_leading_whitespace(self)
- test_replace_part_with_missing_leading_whitespace(self)
- test_replace_part_with_just_some_missing_leading_whitespace(self)
- test_replace_part_with_missing_leading_whitespace_including_blank_line(self)
- test_full_edit(self)
- test_full_edit_dry_run(self)
- test_find_original_update_blocks_mupltiple_same_file(self)
### Functions
- mock_send()
- mock_send()

## File: tests/test_io.py
### Class: TestInputOutput
- test_no_color_environment_variable(self)
- test_autocompleter_with_non_existent_file(self)
- test_autocompleter_with_unicode_file(self)

## File: tests/test_sendchat.py
### Class: TestSendChat
- test_send_with_retries_rate_limit_error(self, mock_print, mock_chat_completion_create)
- test_send_with_retries_connection_error(self, mock_print, mock_chat_completion_create)

## File: tests/test_repo.py
### Class: TestRepo
- test_diffs_empty_repo(self)
- test_diffs_nonempty_repo(self)
- test_diffs_between_commits(self)
- test_get_commit_message(self, mock_send)
- test_get_commit_message_strip_quotes(self, mock_send)
- test_get_commit_message_no_strip_unmatched_quotes(self, mock_send)
- test_get_tracked_files(self)
- test_get_tracked_files_with_new_staged_file(self)
- test_get_tracked_files_with_aiderignore(self)
- test_get_tracked_files_from_subdir(self)
- test_noop_commit(self, mock_send)

## File: tests/utils.py
### Class: IgnorantTemporaryDirectory
- __init__(self)
- __enter__(self)
- __exit__(self, exc_type, exc_val, exc_tb)
### Class: ChdirTemporaryDirectory
- __init__(self)
- __enter__(self)
- __exit__(self, exc_type, exc_val, exc_tb)
### Class: GitTemporaryDirectory
- __enter__(self)
- __exit__(self, exc_type, exc_val, exc_tb)
### Functions
- make_repo(path)

## File: tests/test_commands.py
### Class: TestCommands
- setUp(self)
- tearDown(self)
- test_cmd_add(self)
- test_cmd_add_bad_glob(self)
- test_cmd_add_with_glob_patterns(self)
- test_cmd_add_no_match(self)
- test_cmd_add_no_match_but_make_it(self)
- test_cmd_add_drop_directory(self)
- test_cmd_drop_with_glob_patterns(self)
- test_cmd_add_bad_encoding(self)
- test_cmd_git(self)
- test_cmd_tokens(self)
- test_cmd_add_from_subdir(self)
- test_cmd_add_from_subdir_again(self)
- test_cmd_commit(self)
- test_cmd_add_from_outside_root(self)
- test_cmd_add_from_outside_git(self)
- test_cmd_add_filename_with_special_chars(self)
- test_cmd_add_abs_filename(self)
- test_cmd_add_quoted_filename(self)
- test_cmd_add_existing_with_dirty_repo(self)
- test_cmd_add_unicode_error(self)
- test_cmd_add_drop_untracked_files(self)

## File: tests/test_models.py
### Class: TestModels
- test_max_context_tokens(self)
- test_openrouter_model_properties(self, mock_model_list)

## File: tests/test_main.py
### Class: TestMain
- setUp(self)
- tearDown(self)
- test_main_with_empty_dir_no_files_on_command(self)
- test_main_with_empty_dir_new_file(self)
- test_main_with_empty_git_dir_new_file(self, _)
- test_main_with_empty_git_dir_new_files(self, _)
- test_main_with_dname_and_fname(self)
- test_main_with_subdir_repo_fnames(self, _)
- test_main_with_git_config_yml(self)
- test_main_with_empty_git_dir_new_subdir_file(self)
- test_setup_git(self)
- test_check_gitignore(self)
- test_main_git_ignore(self)
- test_main_args(self)
- test_encodings_arg(self)
### Functions
- side_effect()

## File: tests/test_coder.py
### Class: TestCoder
- setUp(self)
- tearDown(self)
- test_allowed_to_edit(self)
- test_allowed_to_edit_no(self)
- test_allowed_to_edit_dirty(self)
- test_get_last_modified(self)
- test_get_files_content(self)
- test_check_for_filename_mentions(self)
- test_check_for_ambiguous_filename_mentions_of_longer_paths(self)
- test_check_for_subdir_mention(self)
- test_run_with_file_deletion(self)
- test_run_with_file_unicode_error(self)
- test_choose_fence(self)
- test_run_with_file_utf_unicode_error(self)
- test_run_with_invalid_request_error(self, mock_chat_completion_create)
- test_new_file_edit_one_commit(self)
- test_only_commit_gpt_edited_file(self)
- test_gpt_edit_to_dirty_file(self)
- test_gpt_edit_to_existing_file_not_in_repo(self)
### Functions
- mock_send()
- mock_send()
- mock_send()
- mock_send()
- mock_send()
- mock_send()
- mock_get_commit_message(diffs, context)
- mock_send()
- mock_get_commit_message(diffs, context)
- mock_send()
- mock_get_commit_message(diffs, context)

## File: tests/test_wholefile.py
### Class: TestWholeFileCoder
- setUp(self)
- tearDown(self)
- test_no_files(self)
- test_no_files_new_file_should_ask(self)
- test_update_files(self)
- test_update_files_live_diff(self)
- test_update_files_with_existing_fence(self)
- test_update_files_bogus_path_prefix(self)
- test_update_files_not_in_chat(self)
- test_update_files_no_filename_single_file_in_chat(self)
- test_update_files_earlier_filename(self)
- test_update_named_file_but_extra_unnamed_code_block(self)
- test_full_edit(self)
### Functions
- mock_send()

## File: _layouts/default.html

## File: scripts/versionbump.py
### Functions
- main()
- check_branch()
- check_working_directory_clean()
- check_main_branch_up_to_date()


